# Step 2: What changed?

_APIs and programming languages aren't new, so, why the recent hype?_

**They have matured!**

### Modern programming languages and tools

Modern programming languages like JavaScript, Python, Go, Swift, and others are less cumbersome and more flexible than their predecessors.  It used to be that you had to write 10,000 lines of C++ code to do anything useful, but with these modern languages (and packages and libraries available from their developer communities) you can do powerful things in less than 300 lines of code. Which is probably shorter, or on par with, most Cisco IOS configurations that you have worked with.

These languages, when combined with other modern developer tools like:

* Git repositories
* Package management systems
* Virtual environments
* Integrated Development Environments (IDEs)

Equip you with powerful _development tools_ that enable you to automate your tasks and processes and begin creating your own set of powerful tools and workflows.

While these tools are great, and are now bringing rich value to the systems engineering discipline, we are also benefiting from another maturing area of the software development industry...

### Online communities

In the past, when you set out to create some script or program, you often had to start "from scratch," working with low-level standard libraries included with your programming language and toolset of choice. This created a high barrier to entry (and massive global repetition) as software developers had to write the same "heavy lifting" modules to get common tasks done. Take for example making a HTTPS web request (they had to write code to):

* Open a TCP connection on port 443
* Handle TLS negotiation and exchange certificates
* Validate the certificates
* Manage the TCP connection (and any connection pooling)
* Format HTTP requests
* Interpret HTTP responses

That is _a lot_ of work when all the developer wanted to do was get or send some data to or from some remote server; this is why we engineers left this work to the software developers.

Now, thanks to the open source community, social code-sharing and collaboration sites like [GitHub](https://github.com), and public package repositories, the developer communities around these new modern programming languages are building and sharing open source software libraries that help to encourage reuse and reduce duplicate work. Leveraging these community-created libraries can save you tremendous amounts of time and effort, and they enable you to focus your time and effort on what you want your code to do: streamlining your process.

You can make an HTTPS request, without much personal investment, because of the work done by these online communities:

```python
$ pip install requests
Collecting requests
  Using cached https://files.pythonhosted.org/packages/49/df/50aa1999ab9bde74656c2919d9c0c085fd2b3775fd3eca826012bef76d8c/requests-2.18.4-py2.py3-none-any.whl
<-- output omitted for brevity -->
$ python
>>> import requests
>>> requests.get("https://api.github.com")
<Response [200]>
```

_What you are seeing here:_

1. We installed a community library from a public package repository.

    `pip install requests`

2. We entered a Python interactive shell.

    `python`

3. We imported the library into our Python code.

    `import requests`

4. We made an HTTPS request to https://api.github.com.

    `requests.get("https://api.github.com")`

    Which was successful.

    `<Response [200]>`

Starting with installing the [requests](http://docs.python-requests.org/en/master/) package on our machine: in four typed lines in a terminal, we were able to download and install the package and use it to make an HTTPS request (without having to think about the steps involved with making the HTTPS request).

Now that the languages and tools have evolved to be useful to infrastructure engineers, let's see how APIs have become easier to work with.

### API maturity

Gone are the days where it took an expert programmer to work with a product's API. Previous API standards like [SOAP](https://www.w3.org/TR/soap/) proved themselves to be not so "simple," and easier to use API models like _RESTful_ APIs have taken their place.

Now thanks to RESTful APIs and standardized data formats like JSON _(we'll cover these in more depth later)_, you can make requests of your infrastructure with the same ease these modern programming languages provide:

In this example we can use the devnet always on ios xe [sandbox](https://devnetsandbox.cisco.com/RM/Diagram/Index/27d9747a-db48-4565-8d44-df318fce37ad?diagramType=Topology). Note:

Upon running this code you will see `InsecureRequestWarning` This happens when a request is made to an HTTPS URL without certificate verification enabled (not shown for brevity purposes).

```python
>>> import requests
>>>
>>> HOST = 'ios-xe-mgmt.cisco.com'
>>> USER = 'root'
>>> PASS = 'D_Vay!_10&'
>>>
>>>
>>> url = "https://ios-xe-mgmt.cisco.com:9443/restconf/data/ietf-interfaces:interfaces"
>>> headers = {'Content-Type': 'application/yang-data+json',
...                'Accept': 'application/yang-data+json'}
>>>
>>> response = requests.get(url, auth=(USER, PASS), headers=headers, verify=False)
>>>
>>>
>>> interfaces = response.json()
>>> interfaces['ietf-interfaces:interfaces']['interface'][0]['name']
'GigabitEthernet1'
>>> interfaces['ietf-interfaces:interfaces']['interface'][0]['ietf-ip:ipv4']['address'][0]['ip']
'10.10.20.48'
>>>
```

If you are new to coding and Python, and that is hopefully why you are here, this might look a little intimidating; but don't worry, by the end of this track you will understand everything that is going on here - and much more.  For now, we'll suffice it to say:

* In **four statements** (`import requests` through `response = requests.get(...)`) we pulled the interface details from a router.
* In **one statement** (`interfaces = response.json()`) we parsed the data into a format we can use.
* We can then use that data to do whatever we need.

_**Easy!**_  By learning the foundational skills taught in this module, you'll be well on your way to using these powerful tools to automate and create your own programmable tools with your own codified processes.

APIs and programming languages have evolved and matured to the point of being useful and applicable to the domains of infrastructure engineers.

**The net-effect being that you can get powerful things done with relatively small amounts of code**; and by so doing, you can automate the repetitious and/or labor intensive parts of your job freeing you up to focus your time and effort on tasks deserving of your intellect.

**Next step: your future job role**
