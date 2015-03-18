pollutantmean<- function(directory,pollutant,id){
    setwd(directory)
    list.files()->csvs
    sublist<-csvs[id]
    allsum<-0
    allcount<-0
    for(i in sublist){
        record<-read.csv(i)
        polrec<-record[,pollutant]
        rmna<-na.omit(polrec)
        polsum<-sum(rmna)
        polcount<-length(rmna)
        allsum<-allsum+polsum
        allcount<-allcount+polcount
    }
    allsum/allcount
}
