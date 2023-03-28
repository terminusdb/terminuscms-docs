# Squashing Commits

*How-to use the Python client to squash commits in your branch's history.*

Squashing allows you to combine multiple commits in your branch's history into a single commit. This how-to assumes
that you [connected to a database already](../../use-the-clients/python-client/connect-to-a-database.md).

```python
    client.branch = "mybranch"
    commitMessage = "merge all the commits"
    result = client.squash(commitMessage);
}
```

The result will contain the new commit id. You can use it to reset the HEAD to the new
squashed commit.

```python
client.reset(result)
```
