# Building a Terraform Module

This Terraform project aims to create re-usable module. The module to be re-use hosts a static website with AWS S3 buckets. 

## Prerequisites

- AWS Account: You need an active AWS account.
- AWS CLI: Install and configure AWS CLI on your local machine.
- SSH Key Pair: Generate an SSH key pair and place the private key (key.pem) in the private-key directory.
- Terraform: Install Terraform on your local machine.

## Usage

1. Clone this repository to your local machine.


2. Ensure Terraform is installed on your system.

3. Set up your AWS credentials using the AWS CLI:

    ```bash
    aws configure
    ```

4. Modify the c2-variable.tf file to adjust any desired settings such as region, instance type, and key pair.

5. Modify variables in terraform.tfvars and other .tfvars files if needed.

6. Run the following commands in the terminal:

    ```bash
    terraform init
    ```

    ```bash
    terraform validate
    ```

    ```bash
    terraform plan -var-file="secrets.tfvars"
    ```

    ```bash
    terraform apply -var-file="secrets.tfvars"
    ```

## Verify Resources 

1. Verify resources on AWS S3 Bucket dashboard
    
    - Bucket has static website hosting enabled
    - Bucket has public read access enabled using policy
    - Bucket has "Block all public access" unchecked

2. Upload index.html and test

    - Go to AWS Services -> S3 -> Buckets

        + Click on the bucket that was created
        + Click “Upload”
        + Click on “Add files”
        + Path/to/the/the/directory/static-website/index.html

3. Test

    - Go to your browser
        + Endpoint Format test

            ```
            http://example-bucket.s3-website.Region.amazonaws.com/
            ```

        + Replace Values (Bucket Name, Region)
	        
            ```
            http://mybucket-1047.s3-website.us-east-1.amazonaws.com/
            ```     

## Cleanup

- Terraform Destroy

    ```
    terraform plan -destroy  # You can view destroy plan using this command
    ```

    ```
    terraform destroy -auto-approve
    ```

- Clean-Up Files

    ```
    rm -rf .terraform*
    ```

    ```
    rm -rf terraform.tfstate*
    ```

## License

This project is licensed under MIT License.