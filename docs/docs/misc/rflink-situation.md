# The RF Link Phonebook Situation

## The problem

So, the problem is that the Phonebook entries for RF Links is flawed.  I can't remember the specifics without reacquainting myself with a piece of code that I changed a year ago, but basically there are three elements to an RF Link Phonebook Entry.

* Owner callsign
* Description
* Node Number

In the PBX, the Display Name _should_ be:

`owner;description;node`

So extension 15093 should be:

`KC1MUV;International Radio Network;552360`

**The problem** is that the code pulls data out of the database into the Phonebook, like this:

* Owner Callsign: `extension.callsign` = `KC1MUV`
* Extension: `extension.extension` = `15093`
* Link Name: `extension.name.split(";")[0]` = `KC1MUV`
* Allstar Node: `extension.name.split(";")[2]` = `552360`

So the Link Name is being translated incorrectly.

The temporary workaround was to swap the owner and description around so that the Display Name becomes:

`description;owner;node`

So extension 15093 looks like this:

`International Radio Network;KC1MUV;552360`

This renders the Phonebook thus:

* Owner Callsign: `extension.callsign` = `International Radio Network`
* Extension: `extension.extension` = `15093`
* Link Name: `extension.name.split(";")[0]` = `International Radio Network`
* Allstar Node: `extension.name.split(";")[2]` = `552360`

This isn't ideal, and certainly isn't a solution, but it's a workaround for not being able to see the Description of the RF Link.

## The potential solution

I have submitted an untested [Pull Request](https://github.com/hamsoverip/2024-hoip/pull/1) which enacts the following:

```diff
-                    <td>{extension.name.split(";")[0]}</td>
-                    <td>{extension.name.split(";")[2]}</td>
+                    <td>{extension.description}</td>
+                    <td>{extension.allstarNode}</td>
```

This should render the Phonebook (based on how the Display Name _should_ look) like this:

* Owner Callsign: `extension.callsign` = `KC1MUV`
* Extension: `extension.extension` = `15093`
* Link Name: `extension.description` = `International Radio Network`
* Allstar Node: `extension.allstarNode` = `552360`

... which is correct.

From my knowledge and interrogation of the code, the `extension.description` and `extension.allstarNode` values are correctly derived from the Display Name in the PBX.

## Proposed actions

1. My [pull request](https://github.com/hamsoverip/2024-hoip/pull/1) should be **tested** and approved.
2. The Display Names field should be switched back to `owner;description;node` layout, not the `description;owner;node` layout that it was worked-around to be - this is about 5 minutes' work which I'm happy to do across all servers.
3. We _may_ need a full database refresh for the Phonebook.
