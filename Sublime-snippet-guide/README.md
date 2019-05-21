# A Guide to Sublime Text Snippets

Snippets is one of the cool features of Sublime Text. Here is my notes on Sublime Text Snippets to boost my productivity.

Sublime Text Snippets expedite the act of writing code by providing a quick way to insert blocks of text that show up repeatedly in a project. They are both easy to understand and straightforward to write, making them a great tool for saving time and eliminating errors while developing.

A snippet maps a trigger word to a pre-defined block of text, both of which you define. To invoke the snippet, type the trigger word and press `tab`. This simple action expands the trigger word into the mapped block of text — replete with as many brackets, parentheses, and semi-colons as necessary, always matching and in the correct order.

## Creating Snippets

To create a new snippet in Sublime Text 3, go to:

```
Tools -> Developer -> New Snippet...
```

This opens a new window containing a new snippet template, which looks like this:

```xml
<snippet>
  <content><![CDATA[
Hello, ${1:this} is a ${2:snippet}.
]]></content>
  <!-- Optional: Set a tabTrigger to define how to trigger the snippet -->
  <!-- <tabTrigger>hello</tabTrigger> -->
  <!-- Optional: Set a scope to limit where the snippet will trigger -->
  <!-- <scope>source.python</scope> -->
  <!-- Optional: Provide a desription for the snippet -->
  <!-- <description>demo</description> -->
</snippet>
```

There are four parts to a snippet. Although only one part is required, defining all four is recommended.

### 1) The Content (Line 3): Required

```
<content><![CDATA[
  Hello, ${1:this} is a ${2:snippet}.
]]></content>
```

Define the block of text to be expanded by the snippet by editing the line(s) between the `<![CDATA[` and `]]>` tags. (From now on, the block of text that is expanded after the snippet is invoked will be referred to as the snippet’s **content**).

You’ll notice the presence of words surrounded by a dollar sign, braces, numbers, and prefixed by a number. This optional markup specifies a **Field Marker**, which controls the cursor position after the snippet is invoked.

After content is expanded, the cursor moves automatically to the first field marker (`${1:this}` above). Pressing tab again moves the cursor to the next numbered field marker, or to the end of the snippet’s content if there are no fields left (see **pro tip** below).

Text after the colon in a field marker is optional. If specified, it is automatically selected as part of the cursor movement, meaning it can be deleted in one swift stroke. This makes text after the colon great for “placeholder” values that provide guidance of what should be filled in, or for optional default values, such as the `isRequired` field in the example below.

```xml
<content><![CDATA[
  ${1:}: PropTypes.string.${2:isRequired},
]]></content>
```

### Pro tip
Use the `$0` field marker (the exit marker) to explicitly define where the cursor will exit after all field markers have been cycled through. This is useful if you want to rebind the `tab` key to auto-completion after the snippet is invoked. To do so, place the exit marker immediately after the first field marker, like this:`${1:example}$0`

