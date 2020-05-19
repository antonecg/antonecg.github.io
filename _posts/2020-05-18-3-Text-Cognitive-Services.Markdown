---
layout: post
title:  "Text Analytics In PowerBI using Cognitive Services"
date:   2020-05-18 21:03:36 +0530
categories:  Work 
---
Last Year, I gave a talk at TDWI Nashville where I spoke about how to use Azure Cognitive Services to build text analytics dashboards on PowerBI. I've decided to write this blog post to allow other people to do it themselves.
What Are Cognitive Services?

Azure Cognitive Services is Microsoft's attempt to bring pre-trained machine learning models to end users through API's.
I think that it is a promising direction for Microsoft to go in, but I hope that they don't oversell things like IBM did with Watson.
Poking around, it seems that part of cognitive services is an attempt to package some of the great research coming from Microsoft and the scientists that they sponsor.
If you want to play around with the services, I've attached links to the Face API page which lets you look at some of their face recognition services:
•https://azure.microsoft.com/en-us/services/cognitive-services/face/
Here is a link to the Text Analytics API. I will be connecting to the same data below to build a powerbi report:
https://azure.microsoft.com/en-us/services/cognitive-services/text-analytics/
Text Analytics on Power BI

First, import the data that you want to import into your Power BI model. We will write a custom function to call the API and transform a column in power query.
Then, you need to set up a cognitive services account in Azure.
Click on this Link:
https://portal.azure.com/#create/Microsoft.CognitiveServicesAllInOne
Put in your name and location and collect the keys that it will generate.
Now, in PowerBI, go to the query editor window, click home, then new query, then new source, and the blank query.
In the blank query we will input the function below. Put in your API key (instead of xxxxx) and make sure that your endpoint is pointed to the right location. As I am in Nashville, my endpoint is Central US.
Click on the invoke custom function button in the add column section.If you want to dig deeper into how this works, I recommend the article below. In the future, I will be writing more articles on how the text analytics tools they use work and how you could create your own, optimized tools.


•https://westus.dev.cognitive.microsoft.com/docs/services/563879b61984550e40cbbe8d/operations/563879b61984550f30395239


Once you get the hang of it, using text analytics with Power BI is straightforward. Here is the official Microsoft Documentation. The example I will give uses sentiment analysis, but the only difference with the other services will be the last part of the path at the end of the endpoint URL in the function below.




= (text) => let     apikey      = "xxxxxxx",    
endpoint    = "https://centralus.api.cognitive.microsoft.com/text/analytics/v2.1/sentiment",     
jsontext    = Text.FromBinary(Json.FromValue(Text.Start(Text.Trim(text), 5000))),     
jsonbody    = "{ documents: [ { language: ""en"", id: ""0"", text: " & jsontext & " } ] }",    
bytesbody   = Text.ToBinary(jsonbody),     
headers     = [#"Ocp-Apim-Subscription-Key" = apikey],     
bytesresp   = Web.Contents(endpoint, [Headers=headers, Content=bytesbody]),    
jsonresp    = Json.Document(bytesresp),     
sentiment   = jsonresp[documents]{0}[score] in  sentiment

Next, go back to the query with the data you want to transform. 


Next, go back to the query with the data you want to transform. 



Then, name your column. It will ask you about privacy permissions. Select Anonymous log-in and public as the privacy level.





At the end of this process, you should have a text analytics output column. For sentiment, you would have a 0-1 score. For a key phrases service you would have key phrases etc.


https://blogs.technet.microsoft.com/machinelearning/2015/04/08/introducing-text-analytics-in-the-azure-ml-marketplace/
