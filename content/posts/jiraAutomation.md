+++
date = '2026-02-23T18:07:59+05:30'
draft = false
title = 'Jira Automation'
+++

Jira is the most common bug-tracking tool used across the software industry.
There are tasks that need to be done on a daily/weekly/sprint basis, and **Jira provides APIs** to perform many actions on the **issue/user story**.

After I had learned the basics of Python, I was looking for ways to use the knowledge acquired. Since Python is a general-purpose programming language, I thought of automating some repetitive tasks and found Jira. 

In this article, we will be looking on, at how to automate some Jira tasks using Python. You can **use any software/language** to perform the same.

Before proceeding further you need to **identify **whether you are using Jira on **Jira Cloud** or on your **company-hosted** server. Company-hosted Jira would typically have a company name in the domain.

I am using Jira on my company-hosted server. Typically the URL would be 
```
https://jiracompanydomain.com/browse/jiraid
```

Python code snippet for a simple GET request to fetch the given Jira Issue id related details.
```python
import requests
import json
auth = ('username','password')
r = requests.get('https://companydomain.com/rest/api/2/issue/' + jira_id, auth=auth)
summary = r.json()['fields']['summary']
subtasks=r.json()['fields']['subtasks']
print(summary)
print(subtasks)
``` 

To add a comment in a Jira Issue.
```python
import requests
auth = ('username','password')
json_body={
'body':'Need further clarification on this issue'
}
r = requests.post('https://companydomain.com/rest/api/2/issue/' + jira_id +'/comment', auth=auth,json=json_body)
```

These are a few examples that could be done. Personally, I use around 6-7 endpoints to perform/automate my tasks and explore furthermore to see what could be automated.

The most common actions which can be automated are: 
- Fetch Jira issue details.
- Fetch Sub-tasks details.
- Adding comments.
- Adding Work log (Time Spent).
- Attaching a file.
- Creating Fisheye + Crucible Reviews (Uses a different base URL)

You can explore more on Jira APIs in the below links.

[Jira server API documentation](https://docs.atlassian.com/software/jira/docs/api/REST/9.3.1/)

[Jira Cloud API documentation](https://developer.atlassian.com/cloud/jira/software/rest/api-group-issue/)

I wish this would be helpful to automate at least some of your Jira tasks. 
I would be glad to know if you can add any more to this.

What things did you automate in your life?
