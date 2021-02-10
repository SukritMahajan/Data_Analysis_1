# Data_Analysis_1
Learning to plot datasets on R using different plotting function

#setting of the directory 
setwd("/Users/sukritmahajan/Desktop/RNA_Seq_Analysis")

#loading dataset onto RStudio for further processing
data <- read.csv("/Users/sukritmahajan/downloads/R/DESeq_res_G4_APX_OAPX.csv")

#filtering data samples and removing NA 

Adjdata <- data[which(data$pvalue < 0.1 ), ]

baseMean <- c(Adjdata$baseMean, rm.na=TRUE)
log2FoldChange <- c(Adjdata$log2FoldChange, rm.na=TRUE)

#Development of plot using ggplot function 

install.packages(ggplot2)
library(ggplot2)

ggplot(data = Adjdata, aes(x = baseMean, y = log2FoldChange)) + geom_point()
myplot <- ggplot(data = Adjdata, aes(x = baseMean, y = log2FoldChange)) 
myplot + geom_point(color="steelblue")

