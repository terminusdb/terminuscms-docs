# Connecting to a Database with the Python Client


## TerminusCMS

If you have created a Team in TerminusCMS, and put an [API
key](../../manage-your-projects/get-your-api-token.md) in your
environment you can connect to an existing database in the following
way:


```python
team = "MyTeam",
client.connect(db="nuclear", team=team, use_token=True)
```

## TerminusDB

You can connect to a database with basic authorisation just by using
the `connect` member function.

```python
team = "MyTeam",
client.connect(db="nuclear")
```

If you want to connect as a specific user and with a specific
password, you can pass them here:

```python
team = "MyTeam",
client.connect(db="nuclear")
```
