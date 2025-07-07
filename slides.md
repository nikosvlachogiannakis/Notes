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
OR
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

---

# Block Math

$$
\int_0^\infty e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
$$

--

## Above is a mathematical formula.

---

# Vertical slides

This is the parent of vertical slides.

--
## Vertical slide 1

This is a vertical slide under the parent slide.

--
## Vertical slide 2

Another vertical slide under the parent slide.

---

# Add figures

Add a figure with Markdown code

```markdown
    ![Histogram of the solution of a bistable ODE](figures/demo.png)
```

![Histogram](figures/demo.png)

--

or with HTML code for more control

```html
<img src="figures/demo.png" alt="Histogram" width="400">
```

<img src="figures/demo.png" alt="Histogram" width="400">

--

or with percentage

```html
<img src="figures/demo.png" alt="Histogram" style="width:40%">
```

<img src="figures/demo.png" alt="Histogram" style="width:40%">

--

You can add a caption like this
```html
<figure>
  <img src="figures/demo.png" alt="Time series" style="width:70%">
  <figcaption>Figure 1: Histogram of the solution of a bistable ODE</figcaption>
</figure>
```

<figure>
  <img src="figures/demo.png" alt="Time series" style="width:70%">
  <figcaption>Figure 1: Histogram of the solution of a bistable ODE</figcaption>
</figure>

---

# Show a video

```html
<video src="media/video.mp4" autoplay muted loop style="width: 60%"></video>
```

<video src="media/video.mp4" autoplay muted loop style="width: 60%"></video>


---

# Code blocks

<pre><code class="language-python" data-trim>
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
</code></pre>


--

# Code blocks with highlighting

<pre><code class="language-python" data-trim data-line-numbers="3,5-6,10">
import numpy as np
import matplotlib.pyplot as plt

def simulate_ode(f, y0, t):
    """Simple forward Euler ODE solver."""
    y = np.zeros_like(t)
    y[0] = y0
    for i in range(1, len(t)):
        dt = t[i] - t[i-1]
        y[i] = y[i-1] + dt * f(t[i-1], y[i-1])
    return y

# Example usage
f = lambda t, y: -0.5 * y
t = np.linspace(0, 10, 100)
y = simulate_ode(f, 1.0, t)

plt.plot(t, y)
plt.title("Exponential Decay")
plt.xlabel("Time")
plt.ylabel("y(t)")
plt.grid()
plt.show()
</code></pre>


--

<section>
  <h3>Code blocks with animations</h3>

  <div class="fragment">
    <pre><code class="language-python" data-trim data-line-numbers>
import numpy as np
import matplotlib.pyplot as plt
    </code></pre>
  </div>

  <div class="fragment">
    <pre><code class="language-python" data-trim data-line-numbers>
def simulate_ode(f, y0, t):
    """Simple forward Euler ODE solver."""
    y = np.zeros_like(t)
    y[0] = y0
    for i in range(1, len(t)):
        dt = t[i] - t[i-1]
        y[i] = y[i-1] + dt * f(t[i-1], y[i-1])
    return y
    </code></pre>
  </div>

  <div class="fragment">
    <pre><code class="language-python" data-trim data-line-numbers>
f = lambda t, y: -0.5 * y
t = np.linspace(0, 10, 100)
y = simulate_ode(f, 1.0, t)
    </code></pre>
  </div>

  <div class="fragment">
    <pre><code class="language-python" data-trim data-line-numbers>
plt.plot(t, y)
plt.title("Exponential Decay")
plt.xlabel("Time")
plt.ylabel("y(t)")
plt.grid()
plt.show()
    </code></pre>
  </div>
</section>



---

### 🦧 That is all 🦧



