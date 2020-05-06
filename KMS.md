# AWS Key Management Service 

    - It is used to create and manage encryptions keys that are used to encrypt your data. 

    - CMK (Customer Master Key)

    - KSM are regional and can NEVER be exported.

    Key Material ???
        - Use KMS generated key 
        - Your own key material 


* KMS API Calls 

    * IMPORTANT FOR EXAM 

    - aws kms encrypt
    - aws kms decrypt
    - aws kms re-encrypt
    - aws kms enable-key-rotation

* KMS Envelope Encryption 

    - Customer Master Key     ---->       Envelope Key/Data Key        ---->       Data
                            (encrypts)                               (encrypts)

    * The Customer Master Key
        - CMK used to decrypt the data key (envelope key)
        - Envelope Key is used to decrypt the data 







