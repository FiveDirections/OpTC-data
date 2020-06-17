# eCAR - extended Cyber Analytics Repository Model

The extended Cyber Analytics Repository (eCAR) model made by Five Directions is based on MITRE's CAR (https://car.mitre.org/wiki/Data_Model) for describing actions on a host or network. This event-based model is geared toward teams used to ingesting log file style data sources as opposed to graph linked object data.

## The CAR Data Model

CAR defines a three tuple object-action-fields to describe an event. A shortened example of these include:  

Object: file  
Action: open   
Fields: creation_time, file_name, file_path  

## eCAR Model

eCAR adds metadata about an event to provide context and scaling such as host, user, and process information. The object includes:  

timestamp_ms	long int - time since epoch  
id	string - UUID of this object  
hostname	string  
objectID string - UUID of the Object in event  
object	ObjectType   
action	ActionType   
actorID	string - UUID of entity performing the action, generally a process or host  
pid	int - process ID  
tid	int - thread ID  
principal	string - user entity performing the action, sometimes for whom the actor is performing an action on behalf of 
properties	map of strings - key : value of fields  

### Model Semantics

* PID, TID, or PPID of -1 generally means that information is not available  
* PID of 0 and a ProcessID of "00000000-0000-0000-0000-000000000000" also indicates that those details are not available
* When process details are present, an "image_path" entry in Event.properties will also typically be present  

## Example eCAR Object
```
{
  "timestamp": 1539120748904,
  "id": "b9af81fb-066c-4cd6-97cb-b284aabd2d4f",
  "hostname": "VAGRANT-C2FDBFN",
  "objectID": "ece465ca-edf9-48c0-b2be-642ee2dd86d6",
  "object": "PROCESS",
  "action": "CREATE",
  "actorID": "0f0b0dfe-5744-4361-9611-d3a59a1bdfbf",
  "pid": 3648,
  "ppid": 6260,
  "tid": 292,
  "principal": "VAGRANT-C2FDBFN\\vagrant",
  "properties": {
    "parent_image_path": "\\Device\\HarddiskVolume1\\cygwin64\\bin\\bash.exe",
    "user": "VAGRANT-C2FDBFN\\vagrant",
    "command_line": "\"C:\\cygwin64\\bin\\locale.exe\"",
    "image_path": "\\Device\\HarddiskVolume1\\cygwin64\\bin\\bash.exe",
    "sid": "S-1-5-21-23003595-3114578871-2621762399-1000"
  }
}
```


Distribution A: Approved for public release: distribution unlimited
