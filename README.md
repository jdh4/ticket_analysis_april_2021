# Notes

Could not find a way to export emails (tickets) from "Outlook for the web". Used Mac Mail (version 14.0) instead where needed to choose IMAP and incoming/outgoing server as outlook.office365.com (see Settings -> Mail -> Sync email in Outlook).

Messages being 3/31/19:

Sent: 6402  
Inbox: 49,843  

The following shows the keys of a message dictionary:

```
(Pdb) message.keys()
['From', 'To', 'Subject', 'Thread-Topic', 'Thread-Index', 'Date', 'Message-ID', 'References', 'In-Reply-To', 'Content-Language', 'X-MS-Has-Attach', 'X-MS-Exchange-Organization-SCL', 'X-MS-TNEF-Correlator', 'X-MS-Exchange-Organization-RecordReviewCfmType', 'Content-Type', 'MIME-Version']
```

SO: [code](https://stackoverflow.com/questions/33537476/mailbox-to-csv-using-python)
