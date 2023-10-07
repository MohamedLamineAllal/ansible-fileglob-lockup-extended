# ansible-fileglob-lockup-extended
the core `fileglob` lockup extended to be recursive and also hold python glob() function options

Check the following thread in Stackoverflow and my answer for details and context:

- https://stackoverflow.com/a/77251701/7668448

## fileglobr.py

- Does not offer options as you want. It supports recursivity and hidden files by default. Which can give the whole flexibility without having to think about the options.
  - Choose this option. If that is just simple. And it does work in all cases.
  - I didn't put enough thought and testing yet. For now, I created this when I was answering a Stackoverflow question. I'll test and update if there will be anything.

## fileglobe.py

- It offers the options as Python `glob()` function does.

## How to set in your project
- I opted for choosing different names.
  - `fileglobr` (recursive version) no options
  - `fileglobe` (extended) with options  that get passed to Python `glob()`

You will need to add those files as plugins.
- To do so, you will need to create a folder called `lookup_plugins` at the same level as your `playbook`.
- Otherwise use `lookup_plugins={{ ANSIBLE_HOME ~ "/plugins/lookup:/usr/share/ansible/plugins/lookup:our_ansible/lookup_plugins" }}` setting in `ansible.cfg`
  - Refs
    - [Developing plugins](https://docs.ansible.com/ansible/latest/dev_guide/developing_plugins.html)
    - [lockup plugin](https://docs.ansible.com/ansible/latest/plugins/lookup.html#enabling-lookup-plugins)
   
## Usage

Same as the old one but with the new names
- `fileglobr` recursive and without any options
- `fileglobe` the one with options
  - `fileglob('', recursive=True, include_hidden=True)` (not added yet. Will update as soon as i will add it)

## Why wasn't it added and PR

- I didn't evaluate well. I passed fast through all. I have to test and evaluate any possible cases. If all good. I'll push a PR. Or at least check if there was anything in ansible issue track.
