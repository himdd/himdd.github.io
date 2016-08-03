---
layout: post
title:  "��GitHub����ʺ������SSH��Կ"
date:   2016-08-03 09:46:24 +0800
categories: himdd update
---
GitHub��̨������Ӷ��SSH Keys������ͬһ��SSH Keysֻ���������һ���ʺ��ϣ����ʱ��ʾ��Key is already in use���������ɺ������뵽��SSH��Կʹ��ʱ�൱���û������룬������������ͬ���ʺ�ʹ��ͬһ���û������롣Ҫ���ڶ��GitHub�ʺ�����ӹ�Կ����Ҫ�ڱ������ɶ��SSH Keys��ÿ��GitHub�ʺŶ�Ӧһ����ͬ��SSH Keys���������£�

1. ����һ���µ�SSH KEY

{% highlight bash %}
rry@thk:~$ ssh-keygen -t rsa -C 'git@webmaster.me'
Generating public/private rsa key pair.
Enter file in which to save the key (~/.ssh/id_rsa): ~/.ssh/id_rsa2 #��������һ���µ�ssh key�ļ���                           
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in ~/.ssh/id_rsa2.
Your public key has been saved in ~/.ssh/id_rsa2.pub.
The key fingerprint is:
3a:01:17:b3:f9:26:5b:53:b3:69:be:71:a8:66:f6:96 git@webmaster.me
The key's randomart image is:
+--[ RSA 2048]----+
|      o          |
|       =         |
|    . +   o      |
|     . . . +     |
|      o S +      |
|       B + .     |
|      +  .+ +    |
|       .E..+     |
|       +.oo      |
+-----------------+
larry@thk:~$ ssh-add ~/.ssh/id_rsa2
Identity added: ~/.ssh/id_rsa2 (~/.ssh/id_rsa2)
{% endhighlight %}

Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: http://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/

~/.ssh/id_rsa2Ϊ��SSH Keys�ļ���������ʵ������޸ģ���֤ÿ�β�һ�����ɡ�

2. �������ɵ�~/.ssh/id_rsa2.pub�ļ����������������ӵ�GitHub��̨��

3. ��~/.ssh/config�ļ���û���򴴽��������һ��Host��

{% highlight bash %}
#��һ��github�������½����ʺ�ʹ�������������¡�͸���
Host github2
HostName github.com
User git
IdentityFile ~/.ssh/id_rsa2.pub
{% endhighlight %}

4.��GitHub SSH�ֿ��ַ�е�git@github.com�滻���½���Host������

��ԭ��ַ�ǣ�git@github.com:freehost/mail.git���滻��Ӧ���ǣ�github2:freehost/mail.git
������½��Ĳֿ⣬ֱ��ʹ���滻���URL��¡���ɡ�����Ѿ�ʹ��ԭ��ַ��¡���ˣ�����ʹ�������޸ģ�
{% highlight bash %}
git remote set-url origin github2:freehost/mail.git
{% endhighlight %}
