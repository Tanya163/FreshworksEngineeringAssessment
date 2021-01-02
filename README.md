# FreshworksEngineeringAssessment
File based Key-Value data storage
Build a file-based key-value data store that supports the basic CRD (create, read, and delete)operations. This data store is meant to be used as a local storage for one single process on one laptop. The data store must be exposed as a library to clients that can instantiate a class and work with the data store.

## The data store will support the following functional requirements:

1.It can be initialized using an optional file path. If one is not provided, it will reliably create itself in a reasonable location on the laptop.

2.A new key-value pair can be added to the data store using the Create operation. The key is always a string - capped at 32chars. The value is always a JSON object - capped at 16KB.

3.If Create is invoked for an existing key, an appropriate error must be returned.

4.A Read operation on a key can be performed by providing the key, and receiving the value in response, as a JSON object.

5.A Delete operation can be performed by providing the key.

6.Every key supports setting a Time-To-Live property when it is created. This property is optional. If provided, it will be evaluated as an integer defining the number of seconds the key must be retained in the data store. Once the Time-To-Live for a key has expired, the key will no longer be available for Read or Delete operations.

7.Appropriate error responses must always be returned to a client if it uses the data store in unexpected ways or breaches any limits.

## The data store will also support the following non-functional requirements:

1.The size of the file storing data must never exceed 1GB.

2.More than one client process cannot be allowed to use the same file as a data store at any given time.

3.A client process is allowed to access the data store using multiple threads, if it desires to.The data store must therefore be thread-safe.

4.The client will bear as little memory costs as possible to use this data store, whilederiving maximum performance with respect to response times for accessing the data store.

## Following are the steps:
STEP 1: create a code file with create read and delete operation.
STEP 2: Create a test or output file and import the code file in it.
STEP 3:Now after the import you can easily use functions from the main code file in the test file and can test your functions for various operations.

## Languages:
1.Python
## Output
![cap1](https://user-images.githubusercontent.com/76842622/103456293-b8368000-4d1a-11eb-8bc5-67959e362086.PNG)
![cap2](https://user-images.githubusercontent.com/76842622/103456296-ba98da00-4d1a-11eb-883e-6b6ec29d9c71.PNG)

## UPDATE OPERATION CAN ALSO BE IMPLEMENTED:
def updatedata(key,value,time_to_live):

li=storage[key]

if li[1]!=0:

    if time.time()<li[1]:
    
        if key not in storage:
        
            print("Error: given key does not exist in database. Please enter a valid key") #Error message
        
        else:
        
            l=[]
            
            l.append(value)
            
            l.append(li[1])
            
            storage[key]=l
            
    else:
    
        print("Error: time-to-live of",key,"has expired") 
        
else:

    if key not in storage:
    
        print("Error: Key does not exist in database. Please enter a valid key") 
        
    else:
    
        l=[]
        
        l.append(value)
        
        l.append(li[1])
        
        storage[key]=l
        
        print("Value for",key,"updated to",value)
