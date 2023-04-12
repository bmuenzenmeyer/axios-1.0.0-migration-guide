> **Note**
> This UNOFFICIAL guide is created by the community until an official guide can obsolete it. As such, it is full of omissions, "works on my machine" snippets, and situations that may not apply to you. Take this as a note of caution and as an opportunity to improve the guide! With 99 THOUSAND GitHub stars and over 40 MILLION weekly downloads, we have enough energy to get this done.

To add a new migration note, do your best to:

- see if your situation can expand or improve an existing note.
- add a descrete new section with a brief diff of the change.
- use the function name or feature in your changeset so others can find it. `cmd+f` will be our friend
- link to a PR if you have public code.

If you don't have time to do all this, an issue will suffice, we'll do our best to support one another

## Examples

I've copied the [axios 0.X examples from the official repo](https://github.com/axios/axios/tree/v0.x/examples). The thought process is that these might capture common use cases and be useful to check functionality across the `1.X` divide. I've also added the files for both 0.27.2 and 1.3.5 to "`dist/`".

Run `npm start` to load `examples/server.js`. That file currently has a quick and dirty `version` variable that can be switched:

```
  // Process axios itself
  // var version = "0.27.2"
  var version = "1.3.5"
```
