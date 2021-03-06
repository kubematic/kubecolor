# kubecolor

Colorize your kubectl output

* get pods

![image](https://user-images.githubusercontent.com/60682957/95655156-43e7a880-0b40-11eb-9dde-f99f0b34e7a8.png)

* describe pods

![image](https://user-images.githubusercontent.com/60682957/95655177-71345680-0b40-11eb-9003-077e86d24ab1.png)

* something wrong

![image](https://user-images.githubusercontent.com/60682957/95655195-890bda80-0b40-11eb-8688-5d090ec95926.png)

## What's this?

kubecolor colorizes your `kubectl` command output and does nothing else.
kubecolor internally calls `kubectl` command and try to colorizes the output so
you can use kubecolor as a complete alternative of kubectl. It means you can write this in your .bash_profile:

```sh
alias kubectl = kubecolor
```

kubecolor is developed to colorize the output of only READ commands (get, describe...). 
So if the given subcommand was for WRITE operations (apply, edit...), it doesn't give great decorations on it.

For now, not all subcommands are supported and will be done in the future. What is supported can be found below.
Even if what you want to do is not supported by kubecolor now, kubecolor still can just show `kubectl` output without any decorations,
so you don't need to switch kubecolor and kubectl but you always can use kubecolor.

Additionally, if `kubectl` resulted an error, kubecolor just shows the error message in red or yellow.

## Installation

```sh
go get -u github.com/dty1er/kubecolor/cmd/kubecolor
```

## Usage

kubecolor understands every subcommands and options which are available for `kubectl`. What you have to do is just using `kubecolor`
instead of `kubectl` like:

```sh
kubecolor --context=your_context get pods -o json
```

When you don't want to colorize output, you can specify `--plain`. Kubecolor underntands this option and
outputs the result without colorizing. Of course, given `--plain` will never be passed to `kubectl`.
This option will help you when you want to save the output onto a file and edit them by editors.

If you want to make the colorized kubectl default on your shell, just add this line into your shell configuration file:

```sh
alias kubectl = kubecolor
```

## Supported commands

Checked: Supported and works in current latest version
Unchecked: Will be supported but it's still under development
Not in the list: Won't be supported because it's not READ operation

### kubectl commands

- [x] kubectl get
- [x] kubectl top
- [x] kubectl describe
- [ ] kubectl explain
- [ ] kubectl logs
- [ ] kubectl api-rsources
- [ ] kubectl api-versions
- [ ] kubectl version

### format options

- [x] json
- [x] wide
- [x] yaml
- [ ] custom-columns

## Other features which currently unsupported but will be done in the future

- [ ] make it works with -w option
- [ ] Configuring custom colors
- [ ] specifying multiple resources at once (e.g. `kubectl get pod,replicaset`)
  - This will actually work, but if you don't specify "--no-headers" it might look a bit strange.

## Contributions

Always welcome. Just opening an issue should be also greatful.

## LICENSE

MIT
