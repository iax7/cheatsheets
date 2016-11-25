## Request items

Type            | Format
---:            | ---
HTTP Headers    | `Name:Value`
URL parameters  | `name==value`
Data Fields     | `field=value`, `field=@file.txt` serialized as a JSON
Raw JSON fields | `field:=json`, `field:=@file.json`
Form File Fields| `field@/dir/file` (with `--form, -f` only)

## File Transfer
* `http example.org < file.json` Upload
* `http example.org/file > file` Download

## JSON
$ http PUT example.org `name=John` `email=john@example.org`
```
PUT / HTTP/1.1
Accept: application/json, */*
Accept-Encoding: gzip, deflate
Content-Type: application/json
Host: example.org
{
    "name": "John",
    "email": "john@example.org"
}
```

## Default
If your command includes some data request item, or use `--json` or `-j`
```
Content-Type	application/json
Accept	      application/json, */*
```

## Basic Auth
`-a (--auth) username:password`
```
~/.netrc
machine [host] login [user] password [pass]
```

## Redirects
By default, HTTP redirects are not followed and only the first response is shown
`--follow, -F` see the intermediary requests/responses, then use the `--all`

## SSL
`--verify=no`

## Output
Option Flags       | Description
---:               | ---
`--headers`, `-h`	 | Only the response headers are printed.
`--body`, `-b`	   | Only the response body is printed.
`--verbose`, `-v`	 | Print the whole HTTP exchange (request and response). This option also enables --all
`--print=`, `-p`	   | Selects parts of the HTTP exchange. `H` request headers `B` request body `h` response headers `b` response body
