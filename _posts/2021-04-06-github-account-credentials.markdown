---
layout: post
title:  GitHub Authentication Methods (HTTPS/SSH/PAT)
date:   2021-04-06 02:26:28 -0800
categories: blog
---

Everytime you push code to GitHub, you are required to authenticate to your remote repository. GitHub allows the use of different protocols for authentication. Here, I'll provide a short overview for them and you can decide which one is *best* for you.

## SSH
For those new to GitHub, they authenticate using HTTPS. After some time, they wish to improve their account security, and switch to using SSH for authentication. SSH operates on the client-server model for authentication. 


## Personal Authentication Token



## HTTPS 
In the past, GitHub recommended for most to authenticate over HTTPS protocol. The process involves, entering your password, either manually or by a credential helper, and having it sent "over the wire". HTTPS employs **TLS/SSL** to handle communication security. It is **TLS/SSL**'s job to provide confidentiality, authenticity, and integrity to the data being sent to and from the client and server.

In short **TLS/SSL** works as such:
1. Client and server acknowledge each other
2. Agree on a cipher suite
3. Verify the server using the public key and valid certificate
4. Generate session keys
5. Data gets encrypted by the client, sent over, and decrypted by the server using the keys

first clone your repository
{% highlight shell %}
git clone https://github.com/user.name/repository
{% endhighlight %}

There's a common misconception that HTTPS is the more insecure authorization method over the other two. For HTTPS to be compromised, the certificate authorities that signed GitHub's certificate would have to be compromised. The key would then be used to decrypt the session, and your password is left readable in plaintext. (As of TLS 1.3, ciphers that guarantee PFS shall only be used so your past sessions are protected.)
It is very rare for this to occur, and there's also the issue of having your password stored somewhere in plaintext if you wish to push without entering your password each time. Credential helper does have a cache option if you wish to store your password ephemerally.

The other methods are there if you have MFA enabled or wish to remove your password from the process entirely. Though, some networks block SSH so HTTPS and PAT may be the better method in that case.