## instance-information-use-ssm.md

_depencencies_

* aws configure
* python3

_scripts_

```python3
#!/usr/bin/env python3

# instance-information-use-ssm.py

import boto3
client = boto3.client('ssm')


def instanceSessionDataInformations():
    data = client.describe_instance_information()
    return data['InstanceInformationList']


def printInstanceSessionDataInformations():
    data = instanceSessionDataInformations()
    if data != []:
        for instance in data:
            for i, j in instance.items():
                if i != "AssociationOverview" and i != "LastSuccessfulAssociationExecutionDate":
                    print(i.ljust(35), "-", j)
            print("")
    else:
        print("There is no instance of association of ssm manager")


printInstanceSessionDataInformations()

```

_execution_

```bash
python3 instance-information-use-ssm.py
```

_output_

![image](https://user-images.githubusercontent.com/57703276/178131431-3526cead-3184-42dc-bee4-cf53c24b6271.png)