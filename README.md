# PassPushPosh

*PassPushPosh* is a PowerShell Module for interfacing with the [Password Pusher](/pglombardo/PasswordPusher) secure password / string sharing application, primarily through [pwpush.com](https://pwpush.com). It supports creating, retrieving, and deleting anonymous and authenticated pushes, links in any supported language, and getting Push and Dashboard data for authenticated users.

A primary design goal with this module was to provide **simple, beginner-friendly access** to API connections. Cmdlets provide clear responses to errors, support additional messaging via `-Debug` and `-Verbose`, transaction testing via `-Whatif` and `-Confirm`, and in general try to be as "Powershell-y" as possible.

Using *PassPushPosh* can be as simple as:

```powershell
PS> "Here's my secret!" | New-Push | select Link
Link
----
https://pwpush.com/en/p/gzv65wiiuciy
```

Or more completely...

```powershell
PS> Import-Module PassPushPosh
PS> $myPush = New-Push "Here's my secret!"
PS> $myPush.Link
https://pwpush.com/en/p/gzv65wiiuciy
```

See **[Docs](Docs)** or `Get-Help [command]` for more information. Happy sharing!

# Notes

- The 'last call' does not return expired true or expired_on with a datetime, but does show views_remaining = 0.
- For `-Verbose` and `-Debug`, output is sanitized to prevent payloads from being written to screen.

# Links

- [Password Pusher API Documentation](https://pwpush.com/api/1.0.en.html)
- Read-only class properties: [OCRam85:  PowerShell Read Only Class Properties](https://ocram85.com/posts/pwsh-read-only-class-properties/)

# TODO

- [ ] Publish to PowerShell Gallery
- [ ] Support localization (multiple languages)
- [X] Support localization in secret link and 1-step link
- [X] Documentation for [PasswordPush] class
- [ ] Implement automated testing with Pester
- [ ] Implement automatic builds / deploys
- [X] External Module documentation
- [ ] Add PSVersion info to User-Agent
- [ ] Add 'burn after reading' option to `Get-Push` and `New-Push`
- [ ] Issue: [PasswordPush] object Language property reflects global language setting, does not reflect language at time of Push
- [ ] Update `expired` value on a Get-Push call when `views_remaining=0`
