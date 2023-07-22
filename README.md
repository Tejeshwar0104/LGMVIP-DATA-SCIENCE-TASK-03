# LGMVIP-DATA-SCIENCE-TASK-03

CODE:

library(party)
library(dplyr)
library(caTools)

iris 

head(iris)

str(iris)

plot(x=iris$Sepal.Length,y=iris$Sepal.Width,main="SCATTER PLOT FOR SEPAL LENGTH AND SEPAL WIDTH"
     ,xlab="SEPAL LENGTH",ylab="SEPAL WIDTH")

plot(x=iris$Petal.Length,y=iris$Petal.Width,main="SCATTER PLOT FOR PETAL LENGTH AND PETAL WIDTH"
     ,xlab="PETAL LENGTH",ylab="PETAL WIDTH")

sample_data=sample.split(iris,SplitRatio=0.8)
train_data<-subset(iris,sample_data==TRUE)
test_data<-subset(iris,sample_data==FALSE)

model<-ctree(Species~.,train_data)
plot(model)

predict_model<-predict(model,test_data)
predict_model

m_at<-table(test_data$Species,predict_model)
m_at

ac_Test<-sum(diag(m_at))/sum(m_at)
print(paste('Accuracy for test is found to be',ac_Test))
