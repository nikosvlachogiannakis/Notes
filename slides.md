# Presentation slides with Reveal.js

Nikolaos Vlachogiannakis, 2025

---

# How to connect to a Remote Machine?

<pre><code class="language-python" data-trim>
ssh user@remote-server
</code></pre>

--

# OR If you want Passwordless Login

## 1.Generate an SSH key(If you don't have one)

Locally, on your computer, open git Bash:

<pre><code class="language-python" data-trim>
ssh-keygen -t ed25519 -C "your_email@example.com"
</code></pre>
- Press Enter to accept the default path:
C:\Users\YourName\.ssh\id_ed25519
- Choose no passphrase to enable passwordless login


## 2.Copy the Public Key to the Remote Server

<pre><code class="language-python" data-trim>
ssh-copy-id user@remote-server
</code></pre>

--

## 3.Use SSH Config File
Create or edit:
<pre><code class="language-python" data-trim>
~/.ssh/config
</code></pre>
Add:
<pre><code class="language-python" data-trim>
Host myserver
  HostName REMOTE_SERVER
  User USERNAME
  IdentityFile ~/.ssh/id_ed25519
</code></pre>
Now you can simply run:
<pre><code class="language-python" data-trim>
ssh myserver
</code></pre>

## 4.Test the Passwordless SSH Login
<pre><code class="language-python" data-trim>
ssh user@remote-server
</code></pre>
You should be logged in without a password.

---

# Push changes of a Repository on GitHub

- Create a Repository on GitHub(either public or private) with a ReadMe file

- Create a folder:
<pre><code class="language-python" data-trim>
mkdir folder_name
</code></pre>
- Go to its path:
<pre><code class="language-python" data-trim>
cd folder_name
</code></pre>
- Copy the SSH key(ssh_key) from your repository in GitHub:
<pre><code class="language-python" data-trim>
git clone ssh_key
</code></pre>
- You can open the file we cloned in VScode and work on it.

--

# Upload changes in GitHub

<pre><code class="language-python" data-trim>
cd repository_name
</code></pre>

<pre><code class="language-python" data-trim>
git status
</code></pre>

With this command we can see the file that are red, are the files that are changed.
So, we use:
<pre><code class="language-python" data-trim>
git add (all files on red separated by comma)
</code></pre>
**OR**
<pre><code class="language-python" data-trim>
git add .
</code></pre>
Then:
<pre><code class="language-python" data-trim>
git commit -m "This is a message explaining what we changed"
</code></pre>
Finally:
<pre><code class="language-python" data-trim>
git push
</code></pre>
Now, all the changes you made are uploaded in your repository on Github!

--

If we want to check if GitHub is connected with our machine using ssh:
<pre><code class="language-python" data-trim>
ssh -T git@github.com
</code></pre>
and you should get a message like:
<pre><code class="language-python" data-trim>
Hi username!You've successfully authenticated, but GitHub does not provide shell access.
</code></pre>

--

# Additional Information

**SSH** (Secure Shell) is a cryptographic network protocol that allows you to securely connect to remote computers or servers over an unsecured network. It's commonly used for accessing and managing servers, transferring files, and authenticating with services like GitHub. SSH works by using a key pair: a private key stored on your device and a public key shared with the remote service. When you connect, SSH verifies your identity using these keys, ensuring encrypted, secure communication without needing to send passwords.

<span style="color:red">This is red</span>

---

### 🦧 That is all 🦧
