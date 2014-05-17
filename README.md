Two-Tailed-t-Test-Automated-Plot
================================

The below procedure converts two samples of (csv) data into two vectors for computation using R, prior to the automated creation of a plot to supplement t-Testing undertaken using the excel analysis tool pak.

x<-read.table("File1.csv")                
y<-(x$V1)                                  
z<-(z$V2)                                   
my<-mean(y)                                    
mz<-mean(z)                                     
sdy<-sd(y)                                          
sdz<-sd(z)                                            

hy<-dnorm(y, mean=my, sd=sdy, log=FALSE)                 
hz<-dnorm(z, mean=mz, sd=sdz log=FALSE)                   

colors <- c("red", "blue")                                   
labels <- c("Set 2", "Set 1", mz, my)                         

plot(z, hz, type="l", lty=1, xlab="Days",                    
  ylab="Density", main="Two tailed t-test of tw sets of time recordings",col="Red", frame.plot = FALSE)
lines(y, hy, type="l", lty=1, col="Blue")                     
