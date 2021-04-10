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

```python
import sys
import mailbox
import csv
from email.header import decode_header

infile = sys.argv[1]
outfile = sys.argv[2]
writer = csv.writer(open(outfile, "w"))

def get_content(part):
    content = ''
    payload = part.get_payload()
    if isinstance(payload, str):
        content += payload
    else:
        for part in payload:
            content += get_content(part)
    return content

writer.writerow(['date', 'from', 'to', 'subject', 'content'])
for index, message in enumerate(mailbox.mbox(infile)):
    content = get_content(message)
    try:
      subj = decode_header(message['subject'])[0][0]
    except:
      subj = ""

    row = [
        message['date'],
        message['from'],
        message['to'],
        subj,
        content
    ]
    writer.writerow(row)
        #message['from'].strip('>').split('<')[-1],
```

A `configure.log` attachment is represented as:

```
------------=_1617991359-13169-8
Content-Type: application/octet-stream; name="configure.log"
Content-Disposition: attachment; filename="configure.log"
Content-Transfer-Encoding: base64
Content-ID: <f_knalydl60>
RT-Attachment: 33445/772237/603565
```
