# Email Reply Parser

EmailReplyParser is a small library to parse plain text email content.

This is what GitHub uses to display comments that were created from
email replies.  This code is being open sourced in an effort to
crowdsource the quality of our email representation.

See the [Ruby docs][rubydocs] for more information.

[rubydocs]: http://rubydoc.info/gems/email_reply_parser/

## Installation

```
$ gem install email_reply_parser
```

## Usage

To parse reply body:

```ruby
parsed_body = EmailReplyParser.parse_reply(email_body)
```

## Known Issues

### Quoted Headers

Quoted headers aren't picked up if the email client breaks it up into multiple
lines.  GMail breaks up any lines over 80 characters for you.

    On <date>, <author>
    wrote:
    > blah

Not to mention that we're searching for "on" and "wrote".  It won't work
with other languages.

Possible solution: Remove "reply@reply.github.com" lines...

### Weird Signatures

Lines starting with `-` or `_` sometimes mark the beginning of
signatures:

    Hello

    --
    Rick

Not everyone follows this convention:

    Hello

    Mr Rick Olson
    Galactic President Superstar Mc Awesomeville
    GitHub

    **********************DISCLAIMER***********************************
    * Note: blah blah blah                                            *
    **********************DISCLAIMER***********************************

## License

MIT
