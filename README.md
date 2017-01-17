# CG.Survey.Data.Management
# This describes how to create the total scores from the survey data from qualtrics
x = read.csv("CG.Survey.Test.csv", header = TRUE)
# Need to create three different data sets containing items
sel = x[,5:6]
aca = x[,7:8]
cc = x[,9:10]
# Now we are creating mean variable for each of the constructs
# We taking the mean to be consistent with excel, because pivot tables cannot take the median
sel.mean = apply(sel, 1, mean); sel.median
aca.mean = apply(aca, 1, mean); aca.median
cc.mean = apply(aca, 1, mean); cc.median
# Now we are adding back each of the variables into the original data set
x$sel.mean =  sel.mean; x
x$aca.mean = aca.mean; x
x$cc.mean = cc.mean; x
# Now we export the data
x = write.csv(x, "x.csv")
