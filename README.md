# Data_Analysis_1
Plotting dataset using ggplot 

#setting of the directory 
setwd("/Users/sukritmahajan/Desktop/RNA_Seq_Analysis")

#loading dataset onto RStudio for further processing
data <- read.csv("/Users/sukritmahajan/downloads/R/DESeq_res_G4_APX_OAPX.csv")

#filtering data samples and removing NA

Adjdata <- data[which(data$pvalue < 0.1 ), ]

baseMean <- c(Adjdata$baseMean, rm.na=TRUE)
log2FoldChange <- c(Adjdata$log2FoldChange, rm.na=TRUE)

#Development of plot 
install.packages(ggplot2)
library(ggplot2)

#Plotting of plot without assigning color as pvalue 
ggplot(data = Adjdata, aes(x = baseMean, y = log2FoldChange)) + geom_point()
myplot <- ggplot(data = Adjdata, aes(x = baseMean, y = log2FoldChange)) 
p1 <- myplot + geom_point(color="Steelblue", size = 0.1) + ggtitle("Plain graph")

#Plotting with color = pvalue 
myplot1 <- ggplot(data = Adjdata, aes(x = baseMean, y = log2FoldChange, color=pvalue)) 
p2 <- myplot1 + geom_point(size = 0.1) + ggtitle ("Assigning color using pvalue") 

#Plotting by providing transparency to the points to allow more points to be visible
myplot2 <- ggplot(data = Adjdata, aes(x = baseMean, y = log2FoldChange, color = pvalue)) 
p3 <- myplot2 + geom_point(alpha = 1/10, size=0.1) +  ggtitle ("With Alpha") 

#Using logarithmic function for x-axis for refining the plot 
myplot3 <- ggplot(data = Adjdata, aes(x = log(baseMean), y = log2FoldChange, color = pvalue, alpha = 1/10)) 
p4 <- myplot3 + geom_point(size=0.1) + ggtitle ("Semi Logarithmic Graph") 

#Plotting all four plots as one image
grid.arrange (p1,p2,p3,p4, nrow = 4, ncol=1) 
