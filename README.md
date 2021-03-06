# utl_do_over_merging_137_datasets
Data analytics. Data management SAS. Merging 137 datasets/tables in less than a second

    ```  Merging 137 datasets  ```
    ```    ```
    ```  Took 0.42 seconds (cached maybe);  ```
    ```    ```
    ```  Do_over macro on end  ```
    ```    ```
    ```    ```
    ```     WORKING CODE (would really be nice if SAS allowed a macro do in open code -DO-OVER is next best thing;  ```
    ```     ======================================================================================================  ```
    ```    ```
    ```       %utlopts; * turns all options off to minimize log;  ```
    ```    ```
    ```       * generate d1-d137 - with a different variable in each dataset;  ```
    ```       %array(ary,values=d1-d137)  ```
    ```       %do_over(ary,phrase=  ```
    ```           data d?_i_ %nrstr(;)  ```
    ```              set sashelp.class(obs=3 keep=name)%nrstr(;)  ```
    ```              d?_i_=?_i_%nrstr(;)  ```
    ```           run%nrstr(;)  ```
    ```       );  ```
    ```    ```
    ```       %utlopts; * turn options back on;  ```
    ```       data want;  ```
    ```          merge d:;  * note ":" this is like a wildcard;   ```
    ```           by name;  ```
    ```       run;quit;  ```
    ```    ```
    ```  see  ```
    ```  https://stackoverflow.com/questions/46609148/merging-or-joining-multiple-files-together-in-sas-wps  ```
    ```    ```
    ```    ```
    ```    ```
    ```  HAVE  ```
    ```    ```
    ```  WORK.D1 total obs=3  ```
    ```    ```
    ```  Obs     NAME      D1  ```
    ```    ```
    ```   1     Alfred      1  ```
    ```   2     Alice       1  ```
    ```   3     Barbara     1  ```
    ```    ```
    ```    ```
    ```  '''  ```
    ```    ```
    ```  WORK.D137 total obs=3  ```
    ```    ```
    ```  Obs     NAME      D137  ```
    ```    ```
    ```   1     Alfred      137  ```
    ```   2     Alice       137  ```
    ```   3     Barbara     137  ```
    ```    ```
    ```    ```
    ```  WANT  ```
    ```    ```
    ```   Merge all 137 on name  ```
    ```    ```
    ```   NOTE: The data set WORK.WANT has 3 observations and 138 variables.  ```
    ```    ```
    ```  Middle Observation(1 ) of WANT - Total Obs 3  ```
    ```    ```
    ```                                Type  Length    Value  ```
    ```   -- CHARACTER --  ```
    ```  NAME                             C    8       Alfred  ```
    ```    ```
    ```    ```
    ```   -- NUMERIC --  ```
    ```  D1                               N    8       1  ```
    ```  D2                               N    8       2  ```
    ```  D3                               N    8       3  ```
    ```  D4                               N    8       4  ```
    ```    ```
    ```  D130                             N    8       130  ```
    ```  D131                             N    8       131  ```
    ```  D132                             N    8       132  ```
    ```  D133                             N    8       133  ```
    ```  D134                             N    8       134  ```
    ```  D135                             N    8       135  ```
    ```  D136                             N    8       136  ```
    ```  D137                             N    8       137  ```
    ```    ```
    ```  *                _               _       _  ```
    ```   _ __ ___   __ _| | _____     __| | __ _| |_ __ _  ```
    ```  | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |  ```
    ```  | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |  ```
    ```  |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|  ```
    ```    ```
    ```  ;  ```
    ```    ```
    ```    %utlnopts;  ```
    ```  * create 137 datasets;  ```
    ```    proc datasets lib=work;  ```
    ```      delete d:;  ```
    ```    run;quit;  ```
    ```    ```
    ```    %utlnopts;  ```
    ```    %array(ary,values=d1-d137)  ```
    ```    %do_over(ary,phrase= data d?_i_ %nrstr(;) set sashelp.class(obs=3 keep=name)%nrstr(;)d?_i_=?_i_%nrstr(;)run%nrstr(;));  ```
    ```    ```
    ```  *          _       _   _  ```
    ```   ___  ___ | |_   _| |_(_) ___  _ __  ```
    ```  / __|/ _ \| | | | | __| |/ _ \| '_ \  ```
    ```  \__ \ (_) | | |_| | |_| | (_) | | | |  ```
    ```  |___/\___/|_|\__,_|\__|_|\___/|_| |_|  ```
    ```    ```
    ```  ;  ```
    ```    %utlopts;  ```
    ```    data want;  ```
    ```       merge d:;  ```
    ```        by name;  ```
    ```    run;quit;  ```
    ```    ```
    ```  NOTE: There were 3 observations read from the data set WORK.D1.  ```
    ```  NOTE: There were 3 observations read from the data set WORK.D10.  ```
    ```  NOTE: There were 3 observations read from the data set WORK.D100.  ```
    ```  NOTE: There were 3 observations read from the data set WORK.D101.  ```
    ```  NOTE: There were 3 observations read from the data set WORK.D102.  ```
    ```  NOTE: There were 3 observations read from the data set WORK.D103.  ```
    ```  NOTE: There were 3 observations read from the data set WORK.D104.  ```
    ```    ```
    ```    ```
    ```  NOTE: There were 3 observations read from the data set WORK.D97.  ```
    ```  NOTE: There were 3 observations read from the data set WORK.D98.  ```
    ```  NOTE: There were 3 observations read from the data set WORK.D99  ```
    ```  NOTE: The data set WORK.WANT has 3 observations and 138 variables.  ```
    ```    ```
    ```  NOTE: DATA statement used (Total process
