# Uniform Resource Identifier
A [URI](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier), or Uniform Resource _Identifier_, is a unique character sequence that identifies a resource that is (almost always) accessed via the internet.

URIs come in two main types:
- [URLs](https://en.wikipedia.org/wiki/URL)
- [URNs](https://en.wikipedia.org/wiki/Uniform_Resource_Name)
# URL
There are 8 main parts to a URL, though not all the sections are always present.
![[URLpieces.png]]
Required ones are only `Protocol` and `Domain`.
- `Port` and `Path` have defaults and the others are not required
## The Protocol
The "protocol" (also referred to as the "scheme") is the first component of a URL. It defines the rules by which the data being communicated is displayed, encoded or formatted.
- http
- ftp
- mailto
- https
For example:
- `http://example.com`
- `mailto:noreply@jello.app`
### Not All Schemes Require a “//”
The "http" in a URL is always followed by `://`. All URLs have the colon, but the `//` part is only included for schemes that have an [authority component](https://www.rfc-editor.org/rfc/rfc3986#section-3.2). As you can see above, the `mailto` scheme doesn't use an authority component, so it doesn't need the slashes.
## URL Ports
The port in a URL is a virtual point where network connections are made. Ports are managed by a computer's operating system and are numbered from `0` to `65,535` _(Though port `0` is reserved for the system API)_.
- Whenever you connect to another computer over a network, you're connecting to a specific port on that computer, which is listened to by a program on that computer. 
- A port can only be used by one program at a time, which is why there are so many possible ports.
The port component of a URL is often not visible when browsing normal sites on the internet, because 99% of the time you're using the default ports for the HTTP and HTTPS schemes: `80` and `443` respectively.