# utl-add-a-column-only-if-alice-is-a-student-in-the-class
Add a column only if alice is a student in the class  
    Add a column only if alice is a student in the class                                                         
                                                                                                                 
    github                                                                                                       
    https://tinyurl.com/ssmohr4                                                                                  
    https://github.com/rogerjdeangelis/utl-add-a-column-only-if-alice-is-a-student-in-the-class                  
                                                                                                                 
    sas forum                                                                                                    
    https://tinyurl.com/qp9c4ax                                                                                  
    https://communities.sas.com/t5/SAS-Programming/add-new-columes-with-value-with-if-conditons/m-p/609973       
                                                                                                                 
    *_                   _                                                                                       
    (_)_ __  _ __  _   _| |_                                                                                     
    | | '_ \| '_ \| | | | __|                                                                                    
    | | | | | |_) | |_| | |_                                                                                     
    |_|_| |_| .__/ \__,_|\__|                                                                                    
            |_|                                                                                                  
    ;                                                                                                            
                                                                                                                 
    SASHelp.class total obs=19                                                                                   
                                                                                                                 
      NAME       SEX    AGE  ...                                                                                 
                                                                                                                 
      Alfred      M      14                                                                                      
      Alice       F      13                                                                                      
      Barbara     F      13                                                                                      
      Carol       F      14                                                                                      
    ...                                                                                                          
                                                                                                                 
    *            _               _                                                                               
      ___  _   _| |_ _ __  _   _| |_                                                                             
     / _ \| | | | __| '_ \| | | | __|                                                                            
    | (_) | |_| | |_| |_) | |_| | |_                                                                             
     \___/ \__,_|\__| .__/ \__,_|\__|                                                                            
                    |_|                                                                                          
    ;                                                                                                            
                                                                                                                 
     WORK.WANT total obs=19                                                                                      
                                                                                                                 
      NAME       SEX    AGE    SUBJECT                                                                           
                                                                                                                 
      Alfred      M      14     Math                                                                             
                                                                                                                 
      Alice       F      13     Math   ** subject added because Alice is in class                                
                                       ** will not be added if alice is not in class                             
      Barbara     F      13     Math                                                                             
      Carol       F      14     Math                                                                             
      Henry       M      14     Math                                                                             
      ...                                                                                                        
                                                                                                                 
    *                                                                                                            
     _ __  _ __ ___   ___ ___  ___ ___                                                                           
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                          
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                          
    | .__/|_|  \___/ \___\___||___/___/                                                                          
    |_|                                                                                                          
    ;                                                                                                            
                                                                                                                 
    data _null_;                                                                                                 
      set sashelp.class(keep=name age sex);                                                                      
      if name='Alice' then do;                                                                                   
         rc=dosubl('                                                                                             
            data want;                                                                                           
               set sashelp.class(keep=name age sex);                                                             
               subject="Math";                                                                                   
            run;quit;                                                                                            
         ');                                                                                                     
         stop;                                                                                                   
      end;                                                                                                       
    run;quit;                                                                                                    
                                                                                                                 
