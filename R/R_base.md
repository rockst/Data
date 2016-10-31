# 資料分類 #

* numeric 數值

> x = c(1, 2, 3, 4)

> class(x) #顯示 x 的資料型態為 numeric
  
* integer 整數

> x1 = as.integer(x) # 將 x 由 numeric 轉換為 integer 型態

> class(x1) # integer

* logical 邏輯 TRUE or FALSE

> x = c(1, 2, 3, 4)

> x == 2 # 顯示 FALSE TRUE FALSE TRUE

> !(X < 2) # FALSE TRUE TRUE TRUE

> which(x<2) # 1

> is.logical(x) # FALSE

* character / String

> x = c("I", "Love", "R")

> class(X) # character

> length(x) # 顯示 x 維度 3

> nchar(x) # 顯示每個元素的字元個數 1 4 1

> x == "R" # FALSE FALSE TRUE

* factor

> sex = factor(c(1, 1, 0, 0, 1), levels = (0, 1), labels = c("male", "female"))

> sex # 顯示 female female male male female
