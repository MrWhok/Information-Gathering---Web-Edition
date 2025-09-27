# HTB Academy - Information Gathering - Web Edition Write-up

## Table of Contents
1. [whois](#whois)

## whois
## Tools
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

