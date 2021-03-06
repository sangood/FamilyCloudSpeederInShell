# FamilyCloudSpeederInShell

This project has merged to [aiyijing/familycloudaccelerate](https://github.com/aiyijing/familycloudaccelerate), but will update here first.

## Introduction

A shell implementation of FamilyCloudSpeeder, ESurfing, runs properly on almost all linux platform.

## How to Use

### Download the Code

Assuming you've installed git, then

```bash
git clone https://github.com/vcheckzen/FamilyCloudSpeederInShell.git

# CloudDisk
cd FamilyCloudSpeederInShell/CloudDisk

# FamilyCloud
cd FamilyCloudSpeederInShell/FamilyCloud
```

### Get Your Specific Parameters

Fill in the `config.json` file, following [this](https://github.com/MegatronKing/HttpCanary/tree/master/docs/v2/zh-CN#22-%E7%AC%AC%E4%B8%89%E6%96%B9app%E6%8A%93%E5%8C%85) and [this guide](https://github.com/vcheckzen/FamilyCloudSpeederInShell/issues/5).

### Install Requirements and Test Environment

```bash
# Requirements on OpenWRT, Padavan and other RouterOS based on entware or optware environment
opkg update && \
opkg install coreutils-nohup libreadline libcurl libopenssl bash curl wget openssl-util ca-certificates ca-bundle

# Test https and grep, a normal output is like "ip":"121.226.150.154"
curl -s https://ipconfig.io/json | grep -Eo "\"ip\":\"[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\""
wget -qO- https://ipconfig.io/json | grep -Eo "\"ip\":\"[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\""
```

### Run `speedup.sh` to Test

```bash
chmod +x speedup.sh utils.sh
./speedup.sh
```

### Run in Background

Please note that `certail_directory` should be replaced.

```bash
nohup /certail_directory/speedup.sh > /certail_directory/speedup.log 2>&1 &
```

### Auto Run on System Boot

You can add nohup command to `/etc/rc.local`, if the file exists in your system.

```bash
echo \
"nohup /certail_directory/speedup.sh > /certail_directory/speedup.log 2>&1 &" \
>> /etc/rc.local
```