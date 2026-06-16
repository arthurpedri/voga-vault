A [domain name](https://en.wikipedia.org/wiki/Domain_name) is part of a URL. It's the part that tells the computer _where the server is located on the internet_ by being converted into a numerical IP address.
- For example, the URL `https://homestarrunner.com/toons` has a hostname of `homestarrunner.com`. The `https://` and `/toons` portions aren't part of the `domain name -> IP address` mapping that we've been talking about.
## How Does DNS Work?
 [ICANN](https://www.icann.org/) is a not-for-profit organization that manages DNS for the entire internet.

Whenever your computer attempts to resolve a domain name, it contacts one of ICANN's ["root nameservers"](https://en.wikipedia.org/wiki/Root_name_server) whose address is included in your computer's networking configuration. From there, that nameserver can gather the domain records for a specific domain name from their distributed DNS database.
