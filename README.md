# HTB Academy - Information Gathering - Web Edition Write-up

## Table of Contents
1. [whois](#whois)
2. [DNS and Subdomains](#dns-and-subdomains)
    1. [Digging DNS](#digging-dns)
    2. [Subdomain Bruteforcing](#subdomain-bruteforcing)

## whois
### Tools
- whois

### Challenges
1. Perform a WHOIS lookup against the paypal.com domain. What is the registrar Internet Assigned Numbers Authority (IANA) ID number?

    We can solve this just by using `whois`.
    ```bash
    whois paypal.com
    ```
    Then we can look in the Registrar IANA ID line.

    ![alt text](assets/whois1.png)

2. What is the admin email contact for the tesla.com domain (also in-scope for the Tesla bug bounty program)?

    Like in the previous, we can solve this using `whois` again.

    ```bash
    whois tesla.com
    ```
    Then we can look in the Registrant Email line.

    ![alt text](assets/whois2.png)

## DNS and Subdomains
### Digging DNS
#### Tools
- dig
- nslookup
- host
- dnsenum
- fierce
- dnsrecon
- theHarvester
- Online DNS Lookup Services

#### Challenges
1. Which IP address maps to inlanefreight.com?

    To solve this we can use `dig` combine with `A` to retrive IPv4 address.

    ```bash
    dig inlanefreight.com A
    ```

    ![alt text](assets/DNS1.png)

2. Which domain is returned when querying the PTR record for 134.209.24.248?

    We can get the answer from the previous image. Here the details.

    ![alt text](assets/DNS2.png)

3. What is the full domain returned when you query the mail records for facebook.com?

    We can combine `dig` with MX to get the full domain when querying the mail record.

    ```bash
    dig facebook.com MX 
    ``` 
    ![alt text](assets/DNS3.png)

### Subdomain Bruteforcing
#### Tools
- dnsenum
- ffuf
- gobuster 
- fierce
- dnsrecon
- amass
- assetfinder	
- puredns

#### Challenges
1. Using the known subdomains for inlanefreight.com (www, ns1, ns2, ns3, blog, support, customer), find any missing subdomains by brute-forcing possible domain names. Provide your answer with the complete subdomain, e.g., www.inlanefreight.com.

    To solve this, we can use dnsenum with SecList wordlist.

    ```bash
    dnsenum --enum inlanefreight.com -f  /home/mrwhok/tools/SecLists/Discovery/DNS/subdomains-top1million-20000.txt
    ```

    Here the output.

    ![alt text](assets/DNS4.png)