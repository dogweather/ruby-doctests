# ruby-doctests
Doctests inspired by Elixir, Rust, and Python

> **Dev status:** Experimenting with [ruby-doctest2](https://github.com/Qqwy/ruby-doctest2) ("The best kind of documentation is documentation that can never go out of date!"). I'm Judging the feasibility of writing an adapter to scan a directory and auto-discover doctests.

[Rust](https://doc.rust-lang.org/rustdoc/write-documentation/documentation-tests.html), [Elixir](https://hexdocs.pm/elixir/main/docs-tests-and-with.html), and [Python](https://wiki.python.org/moin/DocTest) provide Doctests by letting you embed a REPL session in a comment. These are auto-discovered and executed against the current code as part of the test suite. I like them as unit tests because they're faster to write. They're also living documentation—they don't go out of sync easily.

## Elixir Example

```Elixir
@doc """
iex> remove_newlines("a\\nb\\nc")
"a b c"

iex> remove_newlines("a \\nb")
"a b"
"""
def remove_newlines(text) do
  text
  |> String.replace("\n", " ")
  |> clean_multiple_spaces()
end
```

## Python Example

```Python
def end_with_period(text: str) -> str:
    """
    Ensure the given text ends with a period.

    >>> end_with_period("Hello, world")
    'Hello, world.'

    >>> end_with_period("Hello, world.")
    'Hello, world.'

    >>> end_with_period("Hello, world.  ")
    'Hello, world.'

    >>> end_with_period("便利です。")
    '便利です。'

    >>> end_with_period("便利です。   ")
    '便利です。'
    """
    text = text.strip().removesuffix(':')
    return text if text.endswith('.') or text.endswith('。') else text + '.'
```

## Prior Art

|                |                                           |                                           |
|----------------|-------------------------------------------|-------------------------------------------|
|Dest            |https://github.com/Reizar/Dest             |Looks very nice. Uses custom REPL format.  |
|doctest-core    |https://rubygems.org/gems/doctest-core     |                                           |
|minitest-doctest|https://github.com/lauri/minitest-doctest  |Maybe the easiest to integrate w/ Minitest?|
|rdoctest        |https://github.com/stephencelis/rdoctest   |                                           |
|ruby-doctest2   |https://github.com/Qqwy/ruby-doctest2      |                                           |
|rubydoctest     |https://rubygems.org/gems/rubydoctest      |                                           |
|yard-doctest    |https://rubygems.org/gems/yard-doctest     |Updated relatively recently, in 2019.      |

