<h1>Why Didn't My File Unzip?</h1>

<h2>Here's what I did to fix this issue:</h2>

<p>While following the instrucitons to install WordPress, I hit a wall early on that I didn't understand. When I tried to unzip the zipped file folder for WordPress installation, I kept getting the error message "sudo: unzip: command not found."</p>

<p>So I took to the internet!</p>
<p><b>It is highly recommended that you use a website like Stack Overflow or even Reddit to get information from others. This time luckily the AI at the top of the google search was an easy fix, and the first thing I tried, and it worked. But sometimes it will just literally give you incorrect information. </b></p>

<p> So what's the quick and easy fix? What Google said was most likely to be the problem: <b>I did not have the unzip command utility installed.</b></p>

<ol>
  <li>Install the unzip command utility with "sudo apt install unzip"</li>
<li> Run the unzip command utility to unzip your zipped file and install it</li>
</ol>

<p>Now that you have the unzip command properly installed in your VM, you should be able to unzip any files needed in the future by using the command <b> sudo unzip filename.zip.</b></p>

<p>Sometimes the answer is hard to get to and involves hours of research and a lot of trial and error.</p>
<p><b>Sometimes it is really the easiest quick fix.</b></p>

<p>Hopefully this helped! Happy coding! </p>
