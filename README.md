 sudo mkdir -p /usr/local/bin
Onde passo está o futuro 
sudo apt-get install -y build-essential git wget unzip
git clone https://github.com/eth-sri/silq.git # clone the repository
cd silq && ./dependencies.sh && ./build.sh # download dependencies and build project
# [ignore compilation warnings]
path/to/silq/silq
# (expected) error: no input filesTypically not needed: create directory
sudo mkdir -p /usr/local/bin
# make sure the current directory is `/path/to/silq`
sudo ln -s $(pwd)/silq /usr/local/bin/silq
silq
# (expected) error: no input files
# create a file `erroneous` with a type error:
echo "def main(){ x:=H(false); }" > erroneous.slq
silq erroneous.slq # type-check the created file
# Expected error message:
# erroneous.slq:1:13: error: variable 'x' is not consumed
# def main(){ x:=H(false); }
# Create a correct Silq file:
echo "def main(){ x:=H(false); return measure(x); }" > correct.slq
silq correct.slq # type-check the correct file
# [no output]
silq correct.slq --run # run the correct file
# Outputs 0 or 1


