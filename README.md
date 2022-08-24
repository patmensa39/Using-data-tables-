# Using-data-tables-in R programming 
### Using data tables 
### make sure to install all the packages below. 
install.packages("data.table")
installed.packages("httr")
pacman::p_load(datasets, pacman, data.table,httr, tidyverse)

##laoding the data
data <- "https://ndownloader.figshare.com/files/8448380"
### reading the url (united states daily weather by station)
response <- httr::HEAD(data)
### getting the file size in bytes 
httr::headers(response)[["Content-Length"]]

### downloading with data.table
data <- fread(data)

### looking at the data 
head(data)

## filter the rows 
data[siteid == "Rosemount"]

### selecting the data and the siteid columns 
data[, data, siteid]

### filtering the row, selecting the column
data[siteid == "Rosemount", data, siteid]

### filtering the row, selecting the column and summarizing the content 
data[siteid == "Rosemount", mean(data, na.rm = TRUE), by = param]

