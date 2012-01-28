---
layout: post
title: Error Level Analysis
---

{{ page.title }}
================

<p class="meta">2010 - 2012</p>

Note: The error level analysis servers have been turned off. I can no longer provide access to these servers for free.

<img style="margin: 2em auto; display:block;" src="https://s3.amazonaws.com/github_image_storage/576ff2a_enhanced.jpg" width="500" height="571" alt="Original image from valleygirl.com.au" />

Errorlevelanalysis was a project run from 2010 to 2012 to algorithmically determine the autheniticity of photos. It would take an image, process it, and return a copy of the image with the error levels shown through out the image.

In the above example image, the process shows differing error levels    
throughout, strongly suggesting some form of digital         
manipulation. Areas to note are the lips and shirt of the models, as    
well as the eyes. All are at significantly different error levels than  
their surroundings, as shown by the difference in brightness.           

> Error level analysis (ELA) works by intentionally resaving the image
> at a known error rate, such as 95%, and then computing the difference
> between the images. If there is virtually no change, then the cell has
> reached its local minima for error at that quality level. However, if
> there is a large amount of change, then the pixels are not at their
> local minima and are effectively original.

-Neal Krawetz, Ph.D. 
<a title="hackerfactor.com" href="http://www.hackerfactor.com">http://www.hackerfactor.com</a>

This implemenation makes use of the Python Image Library, and libjpeg
(v6.2.0-882.2). ELA is carried out at 95%. Resulting ELA images have had
their brightness enhanced to further seperate differences out.


Built over a lazy weekend with django. Inspired by Neal Krawetz and his
image forensic work.

