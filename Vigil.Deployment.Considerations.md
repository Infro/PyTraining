Things to consider:
    Deploying to GPU Cloud
        https://www.docker.com/blog/deploy-gpu-accelerated-applications-on-amazon-ecs-with-docker-compose/
        https://github.com/NVIDIA/nvidia-container-toolkit
    Dockerizing
        Nvidia Container Toolkey
        --gpus=all
        https://www.docker.com/blog/multi-arch-build-and-images-the-simple-way/
CUDA in a container.
    Intelliectual Propery
        Ensuring the code isn't available at some point (Github Private Repo, Docker with Obfuscation and Encryption, ?)
    Secrets:
        SMTP Server
            Docker Mailserver ? Other ? AWS Stuff
            DKIM
        Web Server
    Docker SMTP server ( MX Testing, SMTP Send Tests, Can we just run our own SMTP server using AWS Services? )


MX Reader Setup with low priority for the domain "Something" and run a SMTP server in AWS.

dsky.ai

weapon@visionsdk.com
greg@visionsdk.com
john@visionsdk.com

#1 Setup AWS
#2 Setup EC2
#3 Deploy HTTP and SMTP Server
# NO Secure Ports!? docker run -d -p 25:25 namshi/smtp
# docker run -d -p 25:25 -p 143:143 -p 587:587 -v /path/to/mailserver-data:/var/mailserver tvial/docker-mailserver:latestdocker

#4 ?Setup FTP Access? or HTTP Post/Json
#5 Clean up codebase


# Performace
    Frame capturing speed differences
    Multi-level attention
        LORA
    https://gist.github.com/yohhoy/f0444d3fc47f2bb2d0e2

# SAM 2
    https://github.com/sachinsshetty/segment-anything-2/blob/experiments/notebooks/video_predictor_example.ipynb
    https://github.com/sachinsshetty/segment-anything-2/tree/experiments



Infro: What is all recommended for an SMTP server setup.
I know of DKIM, the MX record added to DNS, some other dns record neeing to be added and maybe hosting a file on an http server

GitHub Copilot: To set up an SMTP server properly, you need to configure several components to ensure reliable email delivery and security. Here's a detailed list of recommended steps:

1. **MX Records**: Configure Mail Exchange (MX) records in your DNS settings to point to your SMTP server.

2. **SPF Record**: Add a Sender Policy Framework (SPF) record to your DNS to specify which mail servers are allowed to send email on behalf of your domain.

3. **DKIM**: Set up DomainKeys Identified Mail (DKIM) to sign your emails, ensuring their authenticity.

4. **DMARC**: Add a Domain-based Message Authentication, Reporting & Conformance (DMARC) record to your DNS to specify how your domain handles suspicious emails.

5. **Reverse DNS**: Ensure that your server's IP address has a reverse DNS record that matches your domain name.

6. **TLS/SSL**: Configure Transport Layer Security (TLS) to encrypt email traffic between servers.

7. **PTR Record**: Set up a Pointer (PTR) record for reverse DNS lookup.

8. **HELO/EHLO**: Ensure your SMTP server is configured to use a valid HELO/EHLO hostname.

9. **Rate Limiting**: Implement rate limiting to prevent abuse and ensure your server isn't flagged as a spam source.

10. **Monitoring and Logging**: Set up monitoring and logging to track email delivery and troubleshoot issues.

11. **HTTP File for Verification**: Some email providers may require you to host a verification file on your HTTP server to prove domain ownership.

### Example DNS Records

#### MX Record
```
example.com.  IN  MX  10 mail.example.com.
```

#### SPF Record
```
example.com.  IN  TXT "v=spf1 mx -all"
```

#### DKIM Record
```
default._domainkey.example.com.  IN  TXT "v=DKIM1; k=rsa; p=your_public_key"
```

#### DMARC Record
```
_dmarc.example.com.  IN  TXT "v=DMARC1; p=none; rua=mailto:dmarc-reports@example.com"
```

#### PTR Record
```
1.2.3.4.in-addr.arpa.  IN  PTR  mail.example.com.
```

### Example TLS Configuration (Postfix)
```plaintext
smtpd_tls_cert_file=/etc/ssl/certs/mail.example.com.crt
smtpd_tls_key_file=/etc/ssl/private/mail.example.com.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
```

### Example HELO/EHLO Configuration (Postfix)
```plaintext
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = no
smtpd_helo_required = yes
```

### Example Rate Limiting (Postfix)
```plaintext
smtpd_client_message_rate_limit = 100
```

These steps and configurations will help ensure your SMTP server is set up correctly and securely.