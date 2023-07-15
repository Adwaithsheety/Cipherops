# Google Dorks

Title: Google Dorks for Targeted Information Search

People and Accounts:

1.  Search for emails based on a username:

    ```
    "username*com"
    ```
2.  Search for online resumes of a person:

    ```
    inurl:resume "john smith"
    intext:resume "john smith"
    ```
3.  Search for people with a specific job title and location on LinkedIn:

    ```
    site:http://linkedin.com/in "<job title>" ( OR ☏ OR ✆ OR
    ```
4.  Find people within GitHub code:

    ```
    site:http://github.com/orgs/*/people
    ```
5.  Search for lists of attendees or finalists:

    ```
    intitle:final.attendee.list OR inurl:final.attendee.list
    ```
6.  Search for login information on exposed Trello boards:

    ```
    site:http://trello.com password + admin OR username
    ```

Documents:

1.  Search for specific documents within a domain in PDF format:

    ```
    site:<domain> filetype:PDF
    ```
2.  Search for PDF documents containing possible email information within a specific domain:

    ```
    filetype:pdf <domain> "email"
    ```
3.  Search for XLS files within government websites:

    ```
    filetype:xls site:.gov
    ```

Cloud, Buckets, and Databases:

1.  Search for confidential or top-secret documents within open Amazon S3 buckets:

    ```
    site:http://s3.amazonaws.com confidential OR "top secret"
    ```
2.  Search for confidential login information within XLS files on Amazon buckets:

    ```
    s3 site:http://amazonaws.com filetype:xls password
    ```
3.  Search for copies of databases:

    ```
    ext:sql intext:"-- phpMyAdmin SQL Dump"
    ```

Social Media:

1.  Search for a specific tweet shared on other media, excluding Twitter:

    ```
    "text of a tweet" -site:https://twitter.com
    ```
2.  Search for links or information related to a specific username not coming directly from their Twitter timeline:

    ```
    @dutch_osintguy -site:twitter.com/dutch_osintguy
    ```

Please note that these Google Dorks are intended for authorized purposes and should be used responsibly.
