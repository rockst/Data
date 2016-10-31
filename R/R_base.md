# 資料分類 #

* numeric 數值

	x = c(1, 2, 3, 4)
	class(x) #顯示 x 的資料型態為 numeric
	
	as.numeric() # 轉為 numeric
	is.numeric()
  
* integer 整數

	x1 = as.integer(x) # 將 x 由 numeric 轉換為 integer 型態
	class(x1) # integer
	
	as.integer() 轉為 integer
	is.integer()

* logical 邏輯 TRUE or FALSE

	x = c(1, 2, 3, 4)
	x == 2 # 顯示 FALSE TRUE FALSE TRUE
	!(X < 2) # FALSE TRUE TRUE TRUE
	which(x<2) # 1
	
	is.logical(x) # FALSE
	as.logical(x) # 轉為 logical

* character / String

	x = c("I", "Love", "R")
	class(X) # character
	length(x) # 顯示 x 維度 3
	nchar(x) # 顯示每個元素的字元個數 1 4 1
	x == "R" # FALSE FALSE TRUE
	
	is.character(x) # 是否為字元型態
	as.character()

* factor

	sex = factor(c(1, 1, 0, 0, 1), levels = (0, 1), labels = c("male", "female"))
	sex # 顯示 female female male male female
	
## 處理簡單資料 ##

> 使用 MASS 軟體套件的 Insurance 資料集

	library(MASS)		# 載入套件
	data(Insurance)		# 取得資料集
	
	dim(Insurance)		# 取得維度 64 5
	dim(Insurance[1:10,])	# 取得前 10 筆維度 10 5
	dim(Insurance[,2:4])	# 取得2,3,4變數維度 64 3
	dim(Insurance)[1]	# 取得維度向量的第一個元素，即行數 64
	dim(Insurance)[2]	# 取得維度向量的第一個元素，即列數 5
	
> 透過變數篩選

	vars = c("District", "Age")	# 篩選 Districe 和 Age 變數
	Insurance[20:25, vars]		# 取得 20 ~ 25 行的篩選後資料
	
> 變數相關

	names(Insurance)	# 輸出變數名稱
	head(names(Insurance), n=2)	# 輸出前2個變數
	tail(names(Insurance), n=2)	# 輸出後2個變數
	head(Insurance$Age) # 輸出變數 Age 的若干幾筆資料
	
	class(Insurance$Age)	# 顯示 Age 變數類型
	levels(Insurance$Age)	# 顯示 Age 的水準值
	levels(Insurance$Age)[1]	# 顯示 Age 第一個水準值
	levels(Insurance$Age)[1]="young"	# 修改 Age 第一個水準值
	
## 資料抽樣 ##

> sample(x, size, replace = FALSE, prob = NULL)

* x 向量形式的物件
* size 欲取出的樣本個數
* replace 是否可放回抽樣
* prob 取出機率

> 有放回

	# 隨機取出 10 筆有放回資料
	sub1 = sample(nrow(Insurance), 10, replace = T)
	sub1

> prob

	nrow(Insurance) - 1 #63
	rep(0, nrow(Insurance)-1) # 產生 63 個 0
	c(rep(0, nrow(Insurance)-1), 1) # 前 63 個為0, 第 64 個為 1
	
	# 表示除了最後一筆機率為 1 外，其它皆為 0
	prob = c(rep(0, nrow(Insurance)-1), 1)
	
	# 只有最後一筆 64 會被抽到，而且有放回會出現 10 次
	sub2 = sample(nrow(Insurance), 10, replace = T, prob)
	
> 無放回

	sub3 = sample(nrow(Insurance), 10)
	
## 分層抽樣 ##

> MASS 找不到 strta , getdata function

> strta(data, strtanames=NULL, size, method=c("srswor", "srswr", "poisson", "systematic"), pik, description=FALSE)

* data 資料集
* strtanames 變數名稱
* size 樣本數
* method 抽樣方法
	* srswor 無放回 (default)
	* srswr 有放回
	* poisson 卜松
	* systematic 系統抽樣
* pik 機率
* descript 是否顯示基本資訊

## 整群抽樣 ##

> MASS 找不到 cluster function

> cluster(data, clustername, size, method=c(),  method=c("srswor", "srswr", "poisson", "systematic"), pik, description=FALSE)

## Training Dataset and Testing Dataset ##

> Trainning Dataset 訓練集：建立模型

> Testing Dataset 測試集：評價模型

> 3:1

	train_sub = sample(nrow(Insurance), 3/4*nrow(Insurance))	# 從原生資料取出 3/4
	train_data = Insurance[train_sub,]							# 產生訓練集
	test_data = Insurance[-train_sub,]							# 產生測試集
	dim(train_data); dim(test_data)
	