---
title: What is Rhino.Python?
description: This guide is an overview of Python in Rhino.
authors: ['Dan Belcher']
author_contacts: ['dan']
apis: ['RhinoPython']
languages: ['Python']
platforms: ['Windows', 'Mac']
categories: ['Overview']
origin: http://wiki.mcneel.com/developer/python
order: 1
keywords: ['python', 'overview']
layout: toc-guide-page
TODO: 'needs more GHPython info.'
---


...but a better question is...

## What is Python?

[Python](https://www.python.org/) is a *modern programming language*.  It is easier to learn and use than other non-scripting style languages like C#, VB, or C/C++.  Yet it is quite powerful.

You may need Python if you want to:

- Automate a repetitive task in Rhino much faster than you could do manually.
- Perform tasks in Rhino or Grasshopper that you don't have access to in the standard set of Rhino commands or Grasshopper components.
- Generate geometry using algorithms.
- Many, many other things.  It is a programming language after all.

## Why Python?

Rhino already has a scripting language called RhinoScript!  Why should you use Python?  Well, both the Windows and Mac versions of Rhino contain support for the Python scripting language.  Since Rhino Python scripting is available on both platforms, the same Python scripts can run on both breeds of Rhino!

But more importantly: Python is very popular outside of Rhino!  Much of what you learn about Python can be applied in many other domains.

### What version of Python does Rhino use?

Rhino uses Python version 2.7.

## Where can you use Python in Rhino?

Python can be used all over Rhino in many different ways...

#### RhinoScript Style Functions (Windows)

One of the key features of RhinoScript that make it easy to write powerful scripts is a large library of Rhino specific functions that can be called from scripts.  Our python implementation includes a set of similar functions that can be imported and used in any python script for Rhino.  This set of functions is known as the `rhinoscript` package.

Let's compare scripts for letting a user pick two points and adding a line to Rhino...

Here's RhinoScript:

```vbnet
Dim arrStart, arrEnd
arrStart = Rhino.GetPoint("Start of line")
If IsArray(arrStart) Then
  arrEnd = Rhino.GetPoint("End of line")
  If IsArray(arrEnd) Then
    Rhino.AddLine arrStart, arrEnd
  End If
End If
```

compared with Python:

```py
import rhinoscriptsyntax as rs

start = rs.GetPoint("Start of line")
if start:
  end = rs.GetPoint("End of line")
  if end: rs.AddLine(start,end)
```

Yes, different...but similar enough that you should be able to figure out what is happening in python if you've written RhinoScript.

#### RhinoCommon

Using RhinoCommon - Python scripts also have full access to the .NET framework including access to Rhino's RhinoCommon SDK.  A guide of accessing RhinoCommon from Python scripts is at [Using RhinoCommon from Python]({{ site.baseurl}}/guides/rhinopython/using-rhinocommon-from-python).

#### Grasshopper

Via GHPython.  **TODO** More info needed.


---

## Related Topics

- [What are Python and RhinoScriptSyntax?]({{ site.baseurl }}/guides/rhinopython/what-are-python-rhinoscript)
- [Python Basic Syntax]({{ site.baseurl }}/guides/rhinopython/python-statements/)
- [Rhinoscript Syntax in Python]({{ site.baseurl }}/guides/rhinopython/python-rhinoscriptsyntax-introduction/)
- [Rhino.Python Home Page]({{ site.baseurl }}/guides/rhinopython/)
- [Python (homepage)](https://www.python.org/)