# core-dump-collector
Set of tool for grabbing a core dumps with all dependencies needed to debug it anywhere


core_dump_catch.sh    
Bash script you can put into core_pattern to store core dump files anywhere you want (path need to be adjusted inside script)
It will create a core file, log file and will copy program executable which caused a crash.

You need keep in mind that core limits must be adjusted to make it work properly (set it to unlimited)


crash_collector.sh   
Bash script which will analyse core dump file for all dependencies needed to ananlyse it with debbuger on other systems. It will grab all shared libraries open by crashed process and put it into tar.xz archive together with core dump file and executable which caused a crash

Usage:  
    ./crash_collector.sh -c CORE_FILE [-f EXE_PATH ] [ -o OUTPUT_PATH ]  
    
    Arguments description:  
        -c core_file            required, core dump file to analyse  
        -e executable_path      executable path, optional if file is installed  
        -o ouput_path           path where core dump archive should be created  
        -h                      print this help  
        -v                      verbose mode  

Additional dependencies must be installed to get everything working properly:  
    awk, eu-readelf, file, grep, ldd, readelf, sed, tar

