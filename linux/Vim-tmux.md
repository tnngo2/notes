# VIM - Tmux workshop
ref: https://www.youtube.com/watch?v=5r6yzFEXajQ

## Model editing
- Normal mode
- Visual mode
- Highlight mode
- Ex command

```
^E - scroll the window down
^Y - scroll the window up
gg - to the top of the file
G - to the end the file
```

## Secret sauce
- text objects and motions
- dot command

### Text objects
- w - words
- s - sentences
- p - paragraphs
- t - tags

### Motions
- a - all
- i - in
- t - till
- f - find forward
- F - find backword  

### Commands

- d - delete (also cut)
- c - change (delete, then place in insert mode)
- y - yank (copy)
- v - visually select

### Combination
```
{command}{text object or motion}
```
e.g
```
caw
```

```
dd/yy - delete/yank the current line
D/C - delete/change until end of line
^/$ - move to the beginning/end of line
I/A - move to the begining/end of line and insert
O/o - insert above/below current line and insert 
```