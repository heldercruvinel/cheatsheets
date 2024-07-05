# Credits
- [Jaime Vintharas Github](https://github.com/vintharas)
- [Learn Vim VSCode Extension](https://marketplace.visualstudio.com/items?itemName=vintharas.learn-vim)

# Vim

>- **Commands** are actions that have an effect in your editor.
>
>- **Motions** are commands that you use to move around in **Normal mode**.
>
>- **Operators** are commands that let you perform actions to change the content of your editor.


## Words types
Vim distinguishes between **words** and **WORDS**. 

- A **word** in Vim is either a sequence of letters, digits and numbers, OR a sequence of other non-blank characters.

```
these are 4 words
and these below too
,,, ..... ((((( ,.(
```

- **WORD** is a concept of special kinds of words (with letters, digits and numbers) that also include special characters like ., (, {, etc. They are called  in Vim jargon.

```
this is a WORD: Iam_A_WORD(WORD)
this function call sum(2,3) is also a WORD
this array [1,2,3,4,5] is a WORD as well
```

```
type wwww ==> v   v v   v   v
              word. are two words
              word. is one WORD
type WWW  ==> ^     ^  ^   ^
```

## Text Objects

>Text objects are structured pieces of text that describe the parts in a document: words, sentences, quoted text, paragraphs, blocks, (HTML) tags, etc. You can use them in combination with operators to change a word, sentence, paragraph, etc.

**`{a|i}{text-object}`**

`{a|i}`:
- `a` means around
- `i` means inner

>So *i*nner means that it applies to the inner part of a text object, whereas *a*round means that it applies to the complete text object including delimiters (in case of `(`, `{`, `"`, etc) or whitespace in case of words, sentences and paragraphs.

`{text-object}`:
- `w` - word
- `s` - sentence
- `p` - paragraph
- `"` - quotes

```
            |- `a` means around
            |- `i` means inner
           /
          /
         /
        {a|i}{text-object}
                  /
                 /
                | w - word
                | s - sentence
                | p - paragraph
                | " - quotes
```

And then you combine them with an operator like so:

```
{operator}{a|i}{text-object}
```

## Vim Modes
Vim have three modes, **Normal mode**, **Insert mode** and **Visual mode**.

# Nomal Mode 
In that mode, Vim focus solely on `navigation/editing` super fast around the code and editing.

| Command   | Description                       |
| :-------: | :-------------------------------- |
| **`<ESC>` `<CTRL-[>` `<CTRL-C>`** | If in **`Insert mode`** or **`Visual mode`**, returns to **`Normal mode`**     |
| **`h`** | Move **`left ( ← )`** direction     |
| **`j`** | Move **`down ( ↓ )`** direction     |
| **`k`** | Move **`up ( ↑ )`** direction       |
| **`l`** | Move **`right ( → )`** direction    |
| **`w`** | To **`HORIZONTALLY`** move **word** by **word** |
| **`b`** | To **`HORIZONTALLY`** move backwards **word** by **word**    |
| **`W`** | To **`HORIZONTALLY`** move **WORD** by **WORD** |
| **`B`** | To **`HORIZONTALLY`** move backwards **WORD** by **WORD**    |
| **`e`** | To jump to the end of a **word**    |
| **`ge`** | To jump to the end of the previous **word**     |
| **`E`** | To jump to the end of a **WORD**    |
| **`gE`** | To jump to the end of the previous **WORD**     |
| **`f{character}`** | to find the next occurrence of a character in a line. |
| **`;`** | After using `f{character}` you can type `;` to go to the next occurrence of the character (repeating the last character search) |
| **`,`** | After using `f{character}` you can type `;` to go to the previous occurrence of the character (repeating the last character search) |
| **`F{character}`** | to find the previous occurrence of a character. |
| **`t{character}`** | to move the cursor just before the next occurrence of a character. |
| **`T{character}`** | to move the cursor just before the next occurrence of a character but backwards |
| **`0`** | Moves to the first character of a line |
| **`^`** | Moves to the first non-blank character of a line |
| **`$`** | Moves to the end of a line |
| **`g_`** | Moves to the non-blank character at the end of a line |
| **`}`** | jumps entire paragraphs downwards |
| **`{`** | jumps entire paragraphs upwards |
| **`<CTRL-D>`** | lets you move down half a page by scrolling the page |
| **`<CTRL-U>`** | lets you move up half a page also by scrolling |
| **`/{pattern}`** | to search forward, needs to press `ENTER` after command, `{pattern}` is Regex |
| **`?{pattern}`** | to search backwards, needs to press `ENTER` after command, `{pattern}` is Regex |
| **`n`** | after `/{pattern}` or `?{pattern}` to go to the next match |
| **`N`** | to go to the previous match |
| **`?`** | without a pattern changes the direction of the current search and `n` and `N` also change direction. | 
| **`{count}{command}`** | Counts are numbers which let you multiply the effect of a command, ex: `2w`, `5j`, `3f`, `2/cuc` etc |
| **`gd`** | To **g**o to **d**efinition of whatever is under your cursor.. | 
| **`gf`** | To **g**o to a **f**ile in an import. | 
| **`gg`** | To go to the top of the file. |
| **`{line}gg`** | To go to a specific line. |
| **`G`** | To go to the end of the file. |
| **`%`** | Jump to matching `({[]})`. |
| **`d{motion}`** | Delete the text range defined by **motion**, ex: `dw`, `d$`, `d0` etc. |
| **`{operator}{count}{motion}`** | Combine **operator**, **count** and **motion**, ex: `d2w`, `d5j` etc. |
| **`u`** | To **undo** changes. |
| **`<CTRL-R>`** | To **redo** changes. |
| **`dd`**  | To **d**elete a complete line of text. | 
| **`D`**  | To **D**elete from cursor until the end of the line, equal **`d$`**. |
| **`dl`**  | Deletes the character under the cursor. |
| **`dh`**  | Deletes the character before the cursor. |
| **`x`**  | is equivalent to `dl` and deletes the character under the cursor. |
| **`X`**  | is equivalent to `dh` and deletes the character before the cursor. |
| **`c`**  | To **change command** deletes a piece of text from the cursor and then sends you into **Insert mode**, like **`d{motion}i`**. |
| **`cc`** | Change a complete line. |
| **`C`** | Changes from the cursor until the end of the line. |
| **`ch`** | Deletes the character under the cursor and puts you into Insert mode. |
| **`s`** | is equivalent to `ch`, deletes the character under the cursor and puts you into Insert mode. |
| **`r`** | allows you to replace one single character for another. Very handy to fix typos. |
| **`.`** | The **`.`** dot operator allows you to **repeate your last change**. |
| **`{operator}{a\|i}{text-object}`** | Can combine all this three like `ciw`, `ca"`, `ci'` etc. |
| **`y`** | (yank): Copy in Vim jargon. |
| **`p`** | (put): Paste in Vim jargon. |
| **`g~`** | (switch case): Changes letters from lowercase to uppercase and back. Alternatively, use `gu` to make something lowercase and `gU` to make something uppercase. |
| **`~`** | To switch case for a single character. |
| **`>`** | (shift right): Adds indentation. |
| **`<`** | (shift left): Removes indentation. |
| **`=`** | (format code): Formats code. |

# Insert Mode
In that mode Vim focus in `inserting` bits of text and code, just like a normal editor.

| Command   | Description                       |
| :-------: | :-------------------------------- |
| **`i`** | To get into **`Insert mode`**     |

# Visual mode
In that mode Vim focus in `selecting` text.