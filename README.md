<h1>Inception</h1>

<h2>Project Overview</h2>
<p>The <code>inception</code> project is a system administration exercise that aims to broaden your knowledge of system administration by using Docker. You will virtualize several Docker images, creating them in your new personal virtual machine.</p>

<h2>Purpose</h2>
<p>The purpose of this project is to set up a small infrastructure composed of different services under specific rules using Docker and Docker Compose.</p>

<h2>What You Will Learn</h2>
<ul>
    <li>How to use Docker and Docker Compose to create and manage containers.</li>
    <li>How to write Dockerfiles to build custom Docker images.</li>
    <li>How to set up and configure various services such as NGINX, WordPress, and MariaDB.</li>
    <li>How to manage container networks and volumes.</li>
    <li>How to use environment variables for configuration and security.</li>
</ul>

<h2>Project Contents</h2>

<h3>Mandatory Part</h3>
<p>You must implement the following requirements:</p>
<ul>
    <li>Write a Makefile to set up your entire application using <code>docker-compose.yml</code>.</li>
    <li>Use Docker Compose to set up the following services:
        <ul>
            <li>An NGINX container with TLSv1.2 or TLSv1.3 only.</li>
            <li>A WordPress container with php-fpm installed and configured.</li>
            <li>A MariaDB container.</li>
            <li>A volume for the WordPress database.</li>
            <li>A volume for the WordPress website files.</li>
            <li>A Docker network to connect the containers.</li>
        </ul>
    </li>
    <li>Each service must run in its dedicated container with a custom Dockerfile.</li>
    <li>Containers must restart in case of a crash.</li>
    <li>Use environment variables for configuration, stored in a <code>.env</code> file at the root of the <code>srcs</code> directory.</li>
    <li>Configure your domain name to point to your local IP address (e.g., <code>login.42.fr</code>).</li>
    <li>Ensure that the NGINX container is the only entry point to your infrastructure via port 443 using TLSv1.2 or TLSv1.3.</li>
</ul>

<h3>Bonus Part</h3>
<p>The bonus part includes additional features:</p>
<ul>
    <li>Set up Redis cache for your WordPress website.</li>
    <li>Set up an FTP server container pointing to the volume of your WordPress website.</li>
    <li>Create a simple static website in a language of your choice (excluding PHP).</li>
    <li>Set up Adminer.</li>
    <li>Set up an additional service of your choice and justify its usefulness during the defense.</li>
</ul>
<p>The bonus part will only be assessed if the mandatory part is perfect.</p>

<h2>Usage</h2>
<p>To use the <code>inception</code> project, compile it using the provided Makefile and run it to set up the Docker containers and services. Ensure that the domain name is configured correctly to point to your local IP address.</p>

<h2>Conclusion</h2>
<p>The <code>inception</code> project provides an opportunity to learn about Docker, containerization, and system administration. By completing this project, you will gain valuable skills in managing containerized applications and setting up a secure infrastructure.</p>
