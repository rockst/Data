＃ datasets 資料集 #

> 取得 datasets 中所有資料集

	data (package = "datasets")
	
> 瀏覽資料集的概述

	?AirPassengers
	help(AirPassengers)
	
> 下載安裝軟體

	install.packages(AirPassengers)
	library(AirPassengers)
	data(資料集)
	
> 下載安裝 package

	install.packages("package_name", type = "source")
	library(package_name)