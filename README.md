# neutron

Self-hosted server for [Protonmail client](https://github.com/ProtonMail/WebClient).

Demo: http://beta.webmail.emersion.fr (username: `neutron`, passwords: `neutron`)

Keep in mind that Neutron is less secure than ProtonMail: most servers don't
use full-disk encryption and aren't under 1,000 meters of granite rock.
If you use Neutron, make sure to [donate to ProtonMail](https://protonmail.com/donate)!

## Installation

Requirements:
* Go (to build the server)
* Node, NPM (to build the client)

```bash
# Get the code
go get -u github.com/emersion/neutron
cd $GOPATH/src/github.com/emersion/neutron

# Build client
git submodule init
git submodule update
make build-client

# Start server
make start
```

Default credentials:
* Username: `neutron`
* Password: `neutron`
* Mailbox password: `neutron`

## Roadmap

- [ ] Implement dummy server (see [#1](https://github.com/emersion/neutron/issues/1))
- [x] Define backend interface (see https://github.com/emersion/neutron/blob/master/backend/backend.go)
- [ ] Implement IMAP + SMTP interface

## Backends

All backends must implement the [backend interface](https://github.com/emersion/neutron/blob/master/backend/backend.go).

Currently, only a simple memory backend is available. Nothing is saved on disk, everything is destroyed when the server is shut down.

Writing a backend is just a matter of implementing the necessary functions. You can read the [`memory` backend](https://github.com/emersion/neutron/tree/master/backend/memory) to understand how to do that.

## License

MIT
