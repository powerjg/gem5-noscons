# Some notes

## Source, objects, and linking command

How to get the list of c sources and objects:

Add the following code to the bottom of the `src/SConscript` file.
This replaces some of the code there.

Now, when you run `scons ...` in the output directory you should have three files: `sources`, `objects`, and `link_command`.
You must add `--verbose` to the `scons` command to get the right `link_command` file.

```python
gg = Gem5("gem5", with_any_tags("gem5 lib", "main"))

# Function to create a new build environment as clone of current
# environment 'env' with modified object suffix and optional stripped
# binary.
for env in (envs[e] for e in needed_envs):
    for cls in TopLevelMeta.all:
        cls.declare_all(env)


def dumplist(name, lst):
    with open(name, "w") as f:
        f.write("\n".join(lst))


env = envs[list(needed_envs)[0]]
srcs = gg.sources(env)
dumplist("sources", [s.tnode.get_abspath() for s in srcs])
dumplist("objects", [s[0].get_abspath() for s in gg.srcs_to_objs(env, srcs)])

executable, stripped = gg.declare(env)
with open("link_command", "w") as f:
    f.write(
        executable.executor.get_action_list()[0].strfunction(
            executable, [s[0] for s in gg.srcs_to_objs(env, srcs)], env
        )
    )
```

The only thing that's missing is the `base/date.cc`, `base/date.fo`, and adding `base/date.fo` to the linker list.

## External libraries

-Lext/softfloat
Makefile

-Lext/libelf
Makefile

-Lext/nomali
Makefile

-Lext/libfdt
Makefile

-Lext/iostream3
Makefile

-Lext/fputils
Makefile

-Lext/drampower
Makefile

