# Ruby

## RVM

https://rvm.io/
[How to use RVM](https://www.youtube.com/watch?v=cQVb7fHFjSM)

### What is MRI
*Matz's Ruby Interpreter* : Official C implementation of Ruby.

### Trouble with openssl

Sometimes we have some errors with openssl, failing to download through https.
See help according linux distribution:

- Arch : https://wiki.archlinux.org/title/RVM#Troubleshooting

### List ruby version

- List all available to download `rvm list known`
- List all installed version `rvm list rubies`

### How to use another ruby version

`rvm use x.x.x`

### .rvmrc
`gem env gemdir` Affiche le gem *path* du projet
