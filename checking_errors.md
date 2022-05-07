# Checking Errors

## check errors with exeception

```

try {
    $curl_session = curl_init();
    curl_setopt($curl_session,CURLOPT_URL,"http://www.google.com/search?q=zuriremote");
    curl_setopt($curl_session,CURLOPT_RETURNTRANSFER,true);
    curl_setopt($curl_session,CURLOPT_HEADER, false); 

    $response = curl_exec($curl_session);
    curl_close($curl_session);
    echo $response;

} catch (Exception $e) {
    echo 'Error: '. $e->getMessage();
}


```


## check  errors using if else

```
    $curl_session = curl_init();
    curl_setopt($curl_session,CURLOPT_URL,"http://www.google.com/search?q=zuri remote");
    curl_setopt($curl_session,CURLOPT_RETURNTRANSFER,true);
    curl_setopt($curl_session,CURLOPT_HEADER, false); 

    if(curl_exec($curl_session) == false){
        echo 'Error': . curl_error($curl_session);
    }else{
       $response = curl_exec($curl_session);
    }
    curl_close($curl_session);

    echo $response;
   
```