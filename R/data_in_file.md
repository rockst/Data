# 透過檔案存取資料 #

## CSV , TXT ##

> CSV

	setwd("/Users/rockst/Documents/workspace/Data/R/DATA") # 預設 path
	write.csv(Insurance, "Insurance.csv") # 將資料集寫入檔案
	Insur_csv = read.csv("Insurance.csv") # 讀取檔案
	head(Insur_csv)
	Insur_csv1 = read.table("Insurance.csv")
	head(Insur_csv1)
	Insur_csv2 = read.table("Insurance.csv", header = TRUE, sep = ",") # 分隔 ,
	head(Insur_csv2)
	
> TXT

	write.table(Insurance, "Insurance.txt")
	Insur_txt = read.table("Insurance.txt")
	head(Insur_txt)
	Insur_txt2 = read.table("Insurance.txt", header = TRUE, sep = "") # 分隔 ""
	head(Insur_txt2)
	
> EXCEL

>> 最好的方式是將 Excel 轉成 CSV 再讀取

	# windows
	install.packages("RODBC", type = "source")
	library(RODBC)
	channel = odbcConnectExcel(file.choose())
	channel
	sqlTables(channel)
	Insur = sqlFetch(channel, "Sheet1")
	odbcClose(channel)
	head(Insur)
	
	#Linux
	install.packages("gdata", type = "source")
	library(gdata)
	# xlsfle = file.path(path.gdata("gdata"), 'xls', 'excel.xls')
	xlsfile = file.path('/Users/rockst/Documents/workspace/Data/R/DATA', '', 'group.xlsx')
	xlsfile
	excel_file = read.xls(xlsfile)
	
> Database

>> 使用 RODBC

ODBC in R
http://www.ducheneaut.info/connecting-to-a-mysql-database-with-r-on-a-mac/
http://stackoverflow.com/questions/28081640/installation-of-rodbc-on-os-x-yosemite
http://stackoverflow.com/questions/3426523/odbcconnectexcel-function-from-rodbc-package-for-r-not-found-on-ubuntu
http://stackoverflow.com/questions/26210317/installation-of-rodbc-roracle-packages-on-os-x-mavericks
http://stackoverflow.com/questions/3426523/odbcconnectexcel-function-from-rodbc-package-for-r-not-found-on-ubuntu
http://stackoverflow.com/questions/14124994/how-to-add-odbc-to-mamp-on-osx
http://dev.mysql.com/downloads/file/?id=461816
http://www.iodbc.org/dataspace/doc/iodbc/wiki/iodbcWiki/Downloads#Mac%20OS%20X
http://blog.nguyenvq.com/blog/2013/04/06/guide-to-accessing-ms-sql-server-and-mysql-server-on-mac-os-x/
http://stackoverflow.com/questions/20074620/installing-pyodbc-fails-on-osx-10-9-mavericks


