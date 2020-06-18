---
title: "Security Hygiene for Businesses"
layout: post
---

# Business Security Hygiene

## Intro

As a pentester, it's easy to think pentesting is all there is to security.
This is my attempt at opening my eyes and documenting the retinal burns that result .

Most talk of 'cybersecurity' at uni was of Capture-The-Flag (CTF) competitions.
Or it was around hacking vulnerable machines on Hack The Box or VulnHub.
This partly shaped the "pentesting|GTFO" mindset that many uni students have.

Look around in any large organisation with a mature security team and this bubble is quickly burst. 
Their security functions are numerous:

- vulnerability assessments
- integrate security in the DevOps pipeline (_DevSecOps_)
- manage users' identities (_IAM_)
- security education, training & awareness (_SETA_)
- secure networks and infrastructure
- patch and upgrade
- consume, share and action on cyber threat intelligence (_CTI_)
- log, monitor and respond to incidents (Security Operations Centre - _SOC_)
- governance, risk and compliance (_GRC_)
- static application security testing (_SAST_); and, of course, in the corner
- dynamic application security testing (_DAST_)

Clearly, but non-trivially, There's a lot to the field of 'cybersecurity'. SheHacksPurple wrote a fantastic article on jobs in InfoSec, found [here](1). #todo

Anyway, on to my learnings so far on security for organisations.
A separate post on _personal_ security will be elsewhere.

(1)[https://medium.com/bugbountywriteup/jobs-in-information-security-infosec-93a5efc12ca2]

---

## 2-Factor Authentication

If your employees can log in to their work email over the internet with just a password, this is bad. Real bad.

In isolation, passwords can be easy to guess*, stolen** or brute-forced***. Basically, passwords can be a single point of failure leading directly to an account - and eventually total - compromise.

*_`Password1` is usually the first password we successfully guess in our simulated breach exercises (Red Team engagements)._

**_datasets containing passwords or weak hashes get leaked regularly as a result of breaches. Check out [HaveIBeenPwned](2) to see if your email has been compromised in a past breach._

***_thanks to economies of scale and market demand for powerful GPUs   driven by gamers, cryptocurrency miners and machine learning engineers._

### 3 Ways to Prove Yourself

It doesn't have to be this way. There are three factors to authenticate a person, not just one:

1) something they *know*
2) something they *have*
3) something they *are*

Passwords are (1).  
A significant increase in security is achieved by adopting Two Factors for Authentication (2FA), instead of just one. Most use a combination of 1 and 2 above, while others use 2 and 3.

### What You Have - (2)

You can have _apps_ and _devices_.  
Both generally provide One-Time Passcodes (OTP) and come in various forms:

- Receiving an SMS with a short-lived code
- using a time-based OTP (TOTP) generator e.g. Google Authenticator, Authy, RSA SecurID tokens, YubiKey

SMS OTP assumes you _have_ your phone number - a trusted 'device'.  
TOTP assumes you _have_ your device which generates the OTP (smartphone app, RSA token, Yubikey).

The former, **SMS, is considered insecure** because of the ease with which phone numbers can be ported or 'stolen'.  
Thus, **TOTP is the way to go**.

### What You Are - (3)

Fingerprints, Face ID, Iris scanning - any biological feature with sufficient discriminatory power to distinguish one person from most others with sufficient confidence.

Most modern smartphones either have fingerprint scanners or face identifiers as an unlock mechanism. This - something you _are_ - combined with your phone being yours - something you _have_ - mean that accessing services is technically via 2FA.

>In summary, enable 2-Factor Authentication (2FA) on any and every service you can. Start with the critical accounts like domain accounts used to access email and the corporate network.

---

## Backups

Failing hard drives are inevitable.  
If you did not have a copy of the data then, well, it's likely gone*.

Ransomware attacks are one of the biggest cyber attacks in the world today.  Maersk, NHS, Toll, etc. #todo were hit. Small orgs are hit regularly.
If your work computers/servers get 'ransomwared' then the data is likely gone**.

Natural disasters happen, people spill coffee on their laptops, computers get stolen/lost, an excited sysadmin runs `rm -rf --no-preserve-root` on production systems as a dare from the barista in exchange for a lifetime's worth of free lattes, etc.

Having a backup of your systems in the above situations can mean the difference between a slight inconvenience (plus a year's worth of caffeeine) vs accepting your career with computers being over.

*_unless you pay a significant amount for someone to attempt retrieving the data from the physical medium_

**_unless you pay the ransom or hope that it's one of those weak 'reversible' ransomware malware #todo_

Storage is cheap; processes can be automated; and, cost of not having backups can be measurably high.

Encrypt your backups, lest you have a breach from stolen/lost backups. Also, keep a backup of the backups which is disconnected (offline) - to prevent self-propagating malware from destroying your backups - and offsite - to have a chance against mother nature.

>Have encrypted backups of everything you cannot afford to lose, and a disastor recovery (DR) plan which has been tested.  
Have an offline backup of the backups which is kept offsite.

---

## Patch & Upgrade

There exist public databases of known vulnerabilities in software and systems. Some even include exploits for exploiting those vulnerabilities.

Security sofware like Metasploit are known to contain exploits for almost everything with known exploits in one place and easily accessible.

Want to see in action the attack which brought Maersk to a near halt? Kids, do try it at home - no programming knowledge required.

### What To Patch

Everything:

- endpoints (desktops/laptops)
- servers
- networking equipment (routers/firewalls/load balancers, WAFs, VPN gateways)
- mobile devices (smartphones, tablets, TVs)
- anything with an IP address not included above (printers, IoT)

### But There's No Patch

Why?  

1) Is the system no longer supported e.g. Windows XP?  
Upgrade.  
Avoid using end-of-life (EOL) systems. Yes, it costs to upgrade to a newer system - both in money and time. But, the cost is likely to be insignificant comparent to the cost of a breach because of an unpatched vulnerability being exploited in a system which was  discontinued.

2) Does the vendor not provide updates?  
Move to another vendor.  
Stick to reputable vendors who support their systems over time.  
E.g. this is why I prefer to buy Google's Pixel phones if buying Android. Many other manufacturers are notorious for delaying or skipping updates.

Not all is lost. In both cases, a temporary measure can be to apply compensating controls in other places to make it harder to exploit vulnerabilities. E.g. the risk of a new vulnerability in a web technolgy which is pending vendor patching can possibly be mitigated by tightening WAF rules around the web application.

>Keep systems updated and upgraded.  
Have patching management processes in place.
Stick to reputable vendors who promise support.

---

## Security Education, Training & Awareness (SETA)

- Training Employees
  - strong passwords
  - detecting phishing emails
  - security newsletter

---

## Identity & Access Management (IAM)

- Limit access
  - privileges in AD
  - no sharing of accounts

---

## Segmentation

- Securing Wi-Fi
  - separate for guests
  - separate for IoT

---

## Controls

- Security controls
  - endpoints
  - email filtering
  - network perimeter (e.g. Firewalls)
  - DLP
  - encryption - data at rest + transit
  - Detection/logs/monitoring
  - vulnerability scanning
  - remote access (e.g. VPN)

---

## Policies

- Policies
  - BYOD
  - incident response strategy
    - Ransomware
    - lost/stolen devices
    - malware-infected devices
  - Regulatory Compliance
  - access control (who can do what)

---

## Auditing

- Get everything assessed
  - websites
  - external assets
  - internal network
  - Wi-Fi
  - phishing drills
  - mobile apps
  - cloud configuration/setup
  - network perimeter config (e.g. Firewalls)
  - architecture assessment
  - audit your MSP

---

## Further Reading

- Read
  - ATO (AU)
    - https://www.ato.gov.au/General/Online-services/Identity-security/Protecting-your-information/Top-cyber-security-tips-for-businesses/
  - FTC (USA)
    - https://www.ftc.gov/tips-advice/business-center/small-businesses/cybersecurity/basics
    - https://www.ftc.gov/tips-advice/business-center/guidance/start-security-guide-business