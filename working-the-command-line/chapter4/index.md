## User vs Owner when using chmod

On page 48, the author refers to the owner's permissions (the first group),
the group's permissions (the second group), and others' permissions (the third group). I have always
found it helpful to think of them as the **_user's_** permissions (that is, the user to whom the file belongs),
the group's permissions, and others' permissions. That way, when you want to use the chmod command you
won't think that "o" stands for owner when it really stands for other.

For example:

```
$ chmod og+x my-script
```

is much different from

```
$ chmod ug+x my-script
```

If you think of "o" as "owner," you might do the first one and that might not be what you want.

So, in my opinion, the bulleted list in the middle of page 48 should look like this:

- **User:** you
- **Group:** you and anyone else in your "group" (useful if you share a machine or server)
- **Other:** anyone who _isn't_ in your group
