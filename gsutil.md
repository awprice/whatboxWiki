#Introduction

gsutil is a tool written in Python that let's you access the Google Storage cloud from the command line. It allows you to do the following:

+ Creating and deleting buckets.
+ Uploading, downloading, and deleting objects.
+ Listing buckets and objects.
+ Moving, copying, and renaming objects.
+ Editing object and bucket ACLs.

This guide will cover how to install gsutil onto your slot. It won't go into detail in how to set up Google Cloud Platform, however.

#Installation

1. Connect to your slot through [SSH](/wiki/SSH)

2. Create the installation directory for gsutil

        mkdir ~/.config/gsutil

3. Download the gsutil source

        wget https://storage.googleapis.com/pub/gsutil.tar.gz

4. Extract the source and enter the directory

        tar -zxf gsutil.tar.gz; cd gsutil

5. Configure gsutil to work with your Google Cloud Platform. Follow the steps in the configure process, it is self explanatory.

        gsutil config

6. Add the following line to ``~/.bashrc`` to add the executable to your PATH environment variable. This will allow you to simply type ``gsutil`` to use gsutil.

        export PATH=${PATH}:~/.config/gsutil/

7. (Optional) Clean up the setup files.

        cd ..
        rm gsutil.tar.gz

gsutil should now be installed in ``~/.config/gsutil/``. The next part shall detail how one might use it.

#Use

To use gsutil, simply do the following:

        gsutil <command>

To view the list of available commands:

        gsutil help

##Copying file to a Google Cloud Platform Storage Bucket using gsutil

This short guide will detail how to copy a file to a Storage Bucket using gsutil.

1. Create a file to copy to the Storage Bucket.

        touch testfile

2. Copy the file to the Storage bucket using gsutil.

        gsutil cp testfile gs://my_bucket

The file should successfully transfer to the Storage Bucket.

This completed the guide on how to set up gsutil on your slot. 

Full detailed information about gsutil can be found on the [gsutil Tool Page](https://cloud.google.com/storage/docs/gsutil).
