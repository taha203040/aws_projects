## Introducing Today's Project!

In this project, I will demonstrate how to Protect a database using encryption with AWS KMS! The goal is to secure our data with AWS  from hackers or wrong authorization

### ✍️ What are we doing in this step?

In this step, I will Create a KMS key in order to encrypt data in DynamoDb Table

### Tools and concepts

Services I used include KMS and DynamoDBKey concepts I learnt include encryption and controlling the access to the Encrypted Data

### Project reflection

This project took me approximately 45 minsThe most challenging part was giving access to the test user .It was most rewarding to learn the KMS managing the data access accros multiple users with differnet permissions

I chose to do this project today because simplicity of learning

## Encryption and KMS

Encryption is the process of transforming readable data, known as plaintext, into unreadable data, known as ciphertext, which cannot be understood without the correct decryption key. Companies and developers use encryption to protect sensitive data from unauthorized access and reduce the risk of data exposure. Encryption keys are values used by encryption algorithms to encrypt and decrypt data.

AWS KMS is a managed service used to create and securely manage encryption keys. Key management systems are important because they help protect encryption keys, control who can use them, and manage their lifecycle securely. This allows applications and organizations to encrypt and decrypt sensitive data while maintaining proper access control.

Encryption keys are broadly categorized as \*\*symmetric and asymmetric keys\*\*. I set up a \*\*symmetric key\*\* because it uses the same key for both encryption and decryption. Symmetric encryption is generally faster and more efficient for encrypting large amounts of data, which is why we are using it for our DynamoDB table.

![Encryption and KMS](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/716e7f81-84d1-51d6-8945-d4860caebf77_a2b3c4d5)

### ✍️ What are we doing in this step?

In this step, I will Create and Encrypt a DynamoDB using KMS

## Encrypting Data

My encryption key will safeguard data in DynamoDB, which is stored securely and protected from unauthorized access. It helps ensure that sensitive data remains encrypted when stored in the database.

The different encryption options in DynamoDB include AWS-owned keys, AWS managed keys, and customer managed keys. Their differences are based on who owns and manages the encryption key and the level of control provided over the key. I selected a customer managed key because it gives me greater control over the encryption key, including its permissions and lifecycle, allowing me to manage how the data in my DynamoDB table is protected.

### ✍️ What are we doing in this step?

In this step, I will adding data to DynamoDB in order to verify whether we can see the encrypted data

![Encrypting Data](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/716e7f81-84d1-51d6-8945-d4860caebf77_q8r9s0t1)

## Data Visibility

Rather than controlling access to the key directly, KMS manages user permissions through \*\*IAM policies and KMS key policies\*\*. These policies determine which users or roles are allowed to use the key for operations such as encrypting and decrypting data.

Despite encrypting my DynamoDB table, I could still see the table's items because DynamoDB uses transparent data encryption. This means DynamoDB automatically decrypts the data on my behalf when an authorized user or application requests it. Since I have the required permissions to access the table and use the encryption key, DynamoDB retrieves the encrypted data, decrypts it, and displays it in its original readable format. This protects the data at rest while still allowing authorized users and applications to access it normally.

### ✍️ What are we doing in this step?

In this step, I will create a test user in order to test the case where we can give him the full access to DynamoDB but not to KMS key.

![Data Visibility](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/716e7f81-84d1-51d6-8945-d4860caebf77_c0d1e2f3)

## Denying Access

I configured a new IAM user to \*\*test access to my DynamoDB resources and verify how the encryption key affects access\*\*. The permission policy I granted this user is \*\*AmazonDynamoDBFullAccess\*\*, which allows the user to access and manage DynamoDB resources. However, I did not grant this user permissions to access or manage the \*\*KMS encryption key\*\*.

### ✍️ What are we doing in this step?

In this step, I will login into the new user that we create it before to see whether we can view items in the encrypted DynamoDB table.

After accessing the DynamoDB table as the test user, I encountered an \*\*\`Access denied to kms:Decrypt\`\*\* error because we did not grant the test user permission to use the KMS encryption key. As a result, the user could access the DynamoDB table but could not view its encrypted items. This confirmed that the KMS key was working effectively according to the permissions and access controls I configured.

![Denying Access](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/716e7f81-84d1-51d6-8945-d4860caebf77_w0x1y2z3)

## EXTRA: Granting Access

To let my test user use the encryption key, I added \`nextwork-kms-user\` as a key user in the KMS key policy. My key's policy was updated to allow the test user to perform actions such as Encrypt, Decrypt, ReEncrypt, GenerateDataKey, and DescribeKey. This allowed the test user to decrypt and access the encrypted DynamoDB items while still keeping access controlled through the KMS key policy.

Using the test user, I retried the login and was able to access the DynamoDB table and view its items. This confirmed that the updated KMS key policy successfully granted the test user permission to use the encryption key and decrypt the data.

Encryption secures data instead of \*\*relying only on access controls\*\*. I could combine encryption with \*\*IAM policies and KMS key policies\*\* to control who can access the data and protect it even if unauthorized users gain access to the storage system.

![EXTRA: Granting Access](https://nextwork.ai/cheerful_blue_majestic_alligator/uploads/716e7f81-84d1-51d6-8945-d4860caebf77_feffb2fb8)
