Title: linux bash note
Date: 2016-03-27 18:00

## Chapter 7. Tests

1. when *if* and *then* are on same line in a conditon test,
a semicolon must terminate the *if* statement.

<pre><code>
    if [ condition-true ]
    then
        command 1
        command 2
    else
        command 3
        command 4
    fi

    if [ conditon-true ];then
        command 1
        command 2
    fi
</code></pre>

2. Test Operator

File test
> -e file exists  
> -f file is a regular file (not a direcoty)  
> -d file is directory  
> -b file is block device  
> -r file has read permission  
> -w file has write permission  
> -x file has execute permission  
> f1 -nt f2 file f1 is newer than f2  
> f1 -ot f2 file f1 is older than f2  
> !  veverses the sense of the tests above

Integer comparison
> -eq  is equal to   
> -ne  is not equal to  
> -gt  is greater than  
> -ge  greater or equal to  
> -lt  less than  
> -le  less than or equal to  
>  <   less than  
>  <=  less than or equal to  

String comparison
> =  is equal to  
> -z  string is null, has zero length  
> -n  string is not null  
