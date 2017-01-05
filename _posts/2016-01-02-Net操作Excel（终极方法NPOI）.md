---
date: 2016-01-02 09:09:30+00:00
layout: post
title: Net操作Excel（终极方法NPOI）
categories: Web开发
tags:  NET
---
前言
=====
Asp.net/C#操作Excel已经是老生长谈的事情了，可下面我说的这个NPOI操作Excel，应该是最好的方案了，没有之一，使用NPOI能够帮助开发者在没有安装微软Office的情况下读写Office 97-2003的文件，支持的文件格式包括xls, doc, ppt等。NPOI是构建在POI 3.x版本之上的，它可以在没有安装Office的情况下对Word/Excel文档进行读写操作。

方法
=====
先去官网：[http://npoi.codeplex.com/](http://npoi.codeplex.com/){:target="_blank"}下载需要引入dll（可以选择.net2.0或者.net4.0的dll），然后在网站中添加引用。

Asp.Net导出代码：

	NPOI.HSSF.UserModel.HSSFWorkbook book = new NPOI.HSSF.UserModel.HSSFWorkbook();
	NPOI.SS.UserModel.ISheet sheet = book.CreateSheet("test_01");
	// 第一列
	NPOI.SS.UserModel.IRow row = sheet.CreateRow(0);
	row.CreateCell(0).SetCellValue("第一列第一行");
	// 第二列
	NPOI.SS.UserModel.IRow row2 = sheet.CreateRow(1);
	row2.CreateCell(0).SetCellValue("第二列第一行");
	// ...
	// 写入到客户端  
	System.IO.MemoryStream ms = new System.IO.MemoryStream();
	book.Write(ms);
	Response.AddHeader("Content-Disposition",string.Format("attachment; filename={0}.xls", DateTime.Now.ToString("yyyyMMddHHmmssfff")));
	Response.BinaryWrite(ms.ToArray());
	book = null;
	ms.Close();
	ms.Dispose();

Asp.Net导入代码：

	HSSFWorkbook hssfworkbook;
	#region
	public DataTable ImportExcelFile(string filePath)
	{
    	#region//初始化信息
    	try
    	{
        	using (FileStream file = new FileStream(filePath, FileMode.Open, FileAccess.Read))
        	{
            	hssfworkbook = new HSSFWorkbook(file);
        	}
    	}
    	catch (Exception e)
    	{
        	throw e;
    	}
    	#endregion
    	NPOI.SS.UserModel.Sheet sheet = hssfworkbook.GetSheetAt(0);
    	System.Collections.IEnumerator rows = sheet.GetRowEnumerator();
    	DataTable dt = new DataTable();
		for (int j = 0; j < (sheet.GetRow(0).LastCellNum); j++)
    	{
        	dt.Columns.Add(Convert.ToChar(((int)'A') + j).ToString());
    	}
    	while (rows.MoveNext())
    	{
			HSSFRow row = (HSSFRow)rows.Current;
			DataRow dr = dt.NewRow();
			for (int i = 0; i < row.LastCellNum; i++)
			{
				NPOI.SS.UserModel.Cell cell = row.GetCell(i);
				if (cell == null)
				{
					dr[i] = null;
				}
				else
				{
					dr[i] = cell.ToString();  
				}
			}
			dt.Rows.Add(dr);
		}
		return dt;
	}
	#endregion

C#导出Excel：

	public static void WriteExcel(DataTable dt, string filePath)
	{
    	if (!string.IsNullOrEmpty(filePath) && null != dt && dt.Rows.Count > 0)
    	{
        	NPOI.HSSF.UserModel.HSSFWorkbook book = new NPOI.HSSF.UserModel.HSSFWorkbook();
        	NPOI.SS.UserModel.ISheet sheet = book.CreateSheet(dt.TableName);
        	NPOI.SS.UserModel.IRow row = sheet.CreateRow(0);
        	for (int i = 0; i < dt.Columns.Count; i++)
        	{
        		row.CreateCell(i).SetCellValue(dt.Columns[i].ColumnName);
        	}
        	for (int i = 0; i < dt.Rows.Count; i++)
        	{
        		NPOI.SS.UserModel.IRow row2 = sheet.CreateRow(i + 1);
            	for (int j = 0; j < dt.Columns.Count; j++)
            	{
               		row2.CreateCell(j).SetCellValue(Convert.ToString(dt.Rows[i][j]));
            	}	
        	}
        	// 写入到客户端  
        	using (System.IO.MemoryStream ms = new System.IO.MemoryStream())
        	{
            	book.Write(ms);
            	using (FileStream fs = new FileStream(filePath, FileMode.Create, FileAccess.Write))
            	{
               		byte[] data = ms.ToArray();
               		fs.Write(data, 0, data.Length);
               		fs.Flush();
            	}
            	book = null;
        	}
    	}
	}

结论
=====

这样就很简单的解决Excel的操作了，大家可以试试，很好用，如果觉得对您有用请推荐一下，谢谢。

出处：[http://vipstone.cnblogs.com/](http://vipstone.cnblogs.com/){:target="_blank"}
