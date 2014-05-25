Two-Tailed-t-Test-Automated-Plot
================================

The below procedure converts two samples of (csv) data into two vectors for computation using R, prior to the automated creation of a plot to supplement t-Testing undertaken using the excel analysis tool pak.

x<-read.table("File1.csv")                ## Read source two sample (two column) csv file
y<-(x$V1)                                     ## Isolate first sample
z<-(x$V2)                                     ## Isolate second sample
my<-mean(y)                                       ## Find mean of first sample
mz<-mean(z)                                       ## Find mean of second sample
sdy<-sd(y)                                            ## Find standard deviation of first sample 
sdz<-sd(z)                                            ## Find standard deviation of second sample

t<-t.text(y,z)                                            ## Perform T Test on first and second sample vectors
w<-wilcox.test(y,z)                                          ## Perform Wilcox Test on first and second sample vectors

hy<-dnorm(y, mean=my, sd=sdy, log=FALSE)                  ## Normal distribution of first sample
hz<-dnorm(z, mean=mz, sd=sdz log=FALSE)                   ## Normal distribution of second sample

colors <- c("red", "blue")                                ## Colour of lines for plot            
labels <- c("Set 2", "Set 1", mz, my)                     ## Labels to be displated (names of sets and stdev values)    

par(mfrow=c(1,2))                                         ## Define 2 Column, 1 Row Array for display of two charts

plot(z, hz, type="l", lty=1, xlab="Units",                 ## Plot function
  ylab="Density", main="Two tailed t-test of two samples of an independent variable",col="Red", frame.plot = FALSE)
lines(y, hy, type="l", lty=1, col="Blue")                 ## Second set plot overlay    

boxplot(y,z,ylab="Days Lapsed", names=c("First Sample","second Sample"))	      ## Boxplot function
