#  Rust embedded cortex-m Tutorial 

cargo install cargo-generate

cargo generate --git https://github.com/rust-embedded/cortex-m-quickstart

cd app 

## another way 

curl -LO https://github.com/rust-embedded/cortex-m-quickstart/archive/master.zip
unzip master.zip
mv cortex-m-quickstart-master app
cd app

##  Compiler Steps 

tail -n6 .cargo/config.toml

rustup target add thumbv7m-none-eabi

cargo build --target thumbv7m-none-eabi

cargo build 

##  hello world 
cargo build --example hello

### use qemu to verify image 
qemu-system-arm -cpu cortex-m3 -machine lm3s6965evb -nographic -semihosting-config enable=on,target=native -kernel target/thumbv7m-none-eabi/debug/examples/hello

## use qemu to debug 

qemu-system-arm -cpu cortex-m3 -machine lm3s6965evb -nographic -semihosting-config enable=on,target=native -gdb tcp::3333 -S  -kernel target/thumbv7m-none-eabi/debug/examples/hello

## launch gdb 
gdb-multiarch -q target/thumbv7m-none-eabi/debug/examples/hello

### in gdb 
target remote :3333
