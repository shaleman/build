all: stop build add start 

add:
	vagrant box add contiv/centos72 box/centos72.virtualbox.box --force --provider virtualbox
	vagrant box add contiv/centos72 box/centos72.vmware.box --force --provider vmware_desktop 

start:
	vagrant up

stop:
	vagrant destroy -f

build:
	version=$$(cat VERSION) atlas_token="dummy" packer build --only build-vmware,build-virtualbox --force centos72.json

release-build:
	changelog=${GITHUB_RELEASE_URL} version=$$(cat VERSION) atlas_token=${ATLAS_TOKEN} packer build --only release-vmware,release-virtualbox --force centos72.json

ssh: start
	vagrant ssh
