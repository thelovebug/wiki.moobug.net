---
title: "Adding a new extension"
hidden: true
---

==Applications== -> ==Extensions==  
==+ Add Extension== -> ==+ Add New SIP \[chan_pjsip] Extension==

=== "General"

    #### Add Extension section

    * User Extension: `ExtNum`
    * Display Name: `C4LL Firstname`
    * Outbound CID: `"C4LL Firstname" <ExtNum>`
    * Secret: *(don't change this, but make a note of it as it'll need to go back to the ticket requester)*

    > Be aware that some phones - like those manufactured by Polycom - require a shorter password

    #### User Manager Settings section

    Link to a Default User: None

=== "Voicemail"

    #### Voicemail section

    * Enabled: Yes
     * Voicemail Password: `ExtNum`

=== "Advanced"

    #### Add Extension  section

    * Max Contacts: `10`

    Nothing else should need changing or adding.

## Once done

Click [Submit]

If you aren't adding any more extensions at this point, click [Apply Config].
