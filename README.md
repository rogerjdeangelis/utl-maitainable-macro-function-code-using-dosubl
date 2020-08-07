# utl-maitainable-macro-function-code-using-dosubl
Maitainable macro function code using dosubl 
    Maintainable macro function code using dosubl                                                         
                                                                                                          
    github                                                                                                
    https://tinyurl.com/y264s2x6                                                                          
    https://github.com/rogerjdeangelis/utl-maitainable-macro-function-code-using-dosubl                   
                                                                                                          
    Op wants to simplify this code                                                                        
                                                                                                          
    %if &a=9  %then %do; %let b=I; %end;                                                                  
    %if &a=10 %then %do; %let b=J; %end;                                                                  
    %if &a=11 %then %do; %let b=K; %end;                                                                  
    %if &a=12 %then %do; %let b=L; %end;                                                                  
    %if &a=13 %then %do; %let b=M; %end;                                                                  
    %if &a=14 %then %do; %let b=N; %end;                                                                  
    %if &a=15 %then %do; %let b=O; %end;                                                                  
    %if &a=16 %then %do; %let b=P; %end;                                                                  
    %if &a=17 %then %do; %let b=Q; %end;                                                                  
    %if &a=18 %then %do; %let b=R; %end;                                                                  
    %if &a=19 %then %do; %let b=S; %end;                                                                  
    %if &a=20 %then %do; %let b=T; %end;                                                                  
    %if &a=21 %then %do; %let b=U; %end;                                                                  
    %if &a=22 %then %do; %let b=V; %end;                                                                  
    %if &a=23 %then %do; %let b=W; %end;                                                                  
    %if &a=24 %then %do; %let b=X; %end;                                                                  
    %if &a=25 %then %do; %let b=Y; %end;                                                                  
    %if &a=26 %then %do; %let b=Z; %end;                                                                  
    %if &a=27 %then %do; %let b=AA; %end;                                                                 
    %if &a=28 %then %do; %let b=AB; %end;                                                                 
                                                                                                          
    Here is the solution                                                                                  
                                                                                                          
    This solution is just the dosubl implementation of Joe's code                                         
    Joe Matise <snoopy369@GMAIL.COM>                                                                      
                                                                                                          
    %let b = %mapLtr(26);                                                                                 
    %put -- &=b --;                                                                                       
     -- B=Z --                                                                                            
                                                                                                          
    SAS-L                                                                                                 
    https://listserv.uga.edu/cgi-bin/wa?A2=SAS-L;50d441a2.2008a                                           
                                                                                                          
    I wish we could see more solutions using dosubl.                                                      
    With the exception of work done my Joe and Bart                                                       
    (Bartosz Jablonski yabwon@gmail.com)                                                                  
                                                                                                          
    /*                     _                                                                              
    | |__   _____      __ | |_ ___    _ __ _   _ _ __                                                     
    | `_ \ / _ \ \ /\ / / | __/ _ \  | `__| | | | `_ \                                                    
    | | | | (_) \ V  V /  | || (_) | | |  | |_| | | | |                                                   
    |_| |_|\___/ \_/\_/    \__\___/  |_|   \__,_|_| |_|                                                   
                                                                                                          
    */                                                                                                    
                                                                                                          
                                                                                                          
    %let b = %mapLtr(26);                                                                                 
    %put -- &=b --;                                                                                       
                                                                                                          
     -- B=Z --                                                                                            
                                                                                                          
    %let b = %mapLtr(28);                                                                                 
    %put -- &=b --;                                                                                       
                                                                                                          
    -- B=AB --                                                                                            
                                                                                                          
    /*                                 __                  _   _                                          
     _ __ ___   __ _  ___ _ __ ___    / _|_   _ _ __   ___| |_(_) ___  _ __                               
    | `_ ` _ \ / _` |/ __| `__/ _ \  | |_| | | | `_ \ / __| __| |/ _ \| `_ \                              
    | | | | | | (_| | (__| | | (_) | |  _| |_| | | | | (__| |_| | (_) | | | |                             
    |_| |_| |_|\__,_|\___|_|  \___/  |_|  \__,_|_| |_|\___|\__|_|\___/|_| |_|                             
                                                                                                          
    */                                                                                                    
                                                                                                          
    * runs at macro execution time;                                                                       
                                                                                                          
    %macro mapLtr(a);                                                                                     
                                                                                                          
      %dosubl('                                                                                           
       data _null_;                                                                                       
                                                                                                          
         length b $2.;                                                                                    
                                                                                                          
         * see Joes explanation;                                                                          
                                                                                                          
         if &a < 27 then b = byte(64 + mod(&a-1,26)+1);                                                   
         else            b = cats("A",byte(64 + mod(&a-1,26)+1));                                         
                                                                                                          
         call symputx("b",b,"G");                                                                         
                                                                                                          
       run;quit;                                                                                          
                                                                                                          
       %put 11 &=b 11;                                                                                    
                                                                                                          
       ')                                                                                                 
       %put 22 &=b 22;                                                                                    
       &b                                                                                                 
                                                                                                          
    %mend mapLtr;                                                                                         
                                                                                                          
    %symdel a b / nowarn;                                                                                 
                                                                                                          
    %let b = %mapLtr(26);                                                                                 
    %put -- &=b --;                                                                                       
                                                                                                          
                                                                                                          
