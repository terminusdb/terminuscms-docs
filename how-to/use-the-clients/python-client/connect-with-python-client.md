# Connecting with the Python Client

First, you should install the python client. For instructions on
installing see [installation of
python](./install-the-python-client.md).

## Connecting with the Python Client

Depending on whether you are connecting to an instance you have set up
yourself, or whether you are using TerminusCMS in the cloud, there are
two different methods of connection.

In both cases, you should load TerminusDB in your script with the
following:

```python
from terminusdb_client import Client
```

### TerminusCMS

The TerminusCMS endpoint has the form
`https://cloud.terminusdb.com/TEAM/` where `TEAM` is the name of the
team you are using in TerminusCMS for the data products you want to
access.

In order to connect to this team, you will need to [get your API
key](../../manage-your-projects/get-your-api-token.md) after selecting
the team you want to use.

You should put your access token in your environment, using the
environment variable `TERMINUSDB_ACCESS_TOKEN`. This ensures that
scripts do not leak the access token when checked into source control.

```shell
export TERMINUSDB_ACCESS_TOKEN="..."
```

At this point you can connect with the API key using the code:

```
team="MyTeam"
client.connect(team=team, use_token=True)
```

### Connecting to a TerminusDB installation

Whether you are connecting to a local docker, a local server, or on a
server that you've set up somewhere, you can use the following to log
in to TerminusDB.

```shell
team="MyTeam",
client = Client("http://localhost:6363/")
client.connect(team=team, password="MyPassword")
```

If you are using terminusdb locally, and you have not set up a
specific team, or changed the password differently from the default,
you can simply connect with:

```shell
team="admin",
client = Client("http://localhost:6363/")
client.connect(team=team)
```
