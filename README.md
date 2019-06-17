# rein

![rein](https://raw.githubusercontent.com/firstboot/rein/master/rein-logo.png)

This program is used to efficiently redirect connections from one IP address/port combination to another. 

It is useful when operating virtual servers, dockers, firewalls and the like.  It was developed by golang.



### 1. Simple deployment 

#### 1.1 CentOS/RHEL/Ubuntu

```shell
cd ~
wget https://github.com/firstboot/rein/blob/master/release/linux/rein
chmod +x rein
./rein -e > rein.json
# modify rein.json for you
./rein -c rein.json
```

#### 1.2 Windows

- download 2 files

  https://github.com/firstboot/rein/blob/master/release/windows/rein.zip

- decompress `rein.zip`

- generating and modifying conf `rein.json` 

  ```powershell
  # generate default conf 'rein.json'
  rein.exe -e > rein.json
  ```

  ```json
  {
  	"upstream": [
  		{"source": "0.0.0.0:8150", "target": "127.0.0.1:9991"}
  	],
  	"fileshare": [
  		{"port": "9991", "path": "."}
  	]
  }
  ```

- running

  ```powershell
  rein.exe -c rein.json
  ```

  
### 2. Configuration tip

#### 2.1 upstream

`upstream ` include keywords `source` and `target`. 

  `source`  open port  to listen, `target`  is data stream destination.

eg:

```json
{
	"upstream": [
		{"source": "0.0.0.0:8150", "target": "127.0.0.1:9991"}
	]
}
```

#### 2.2 file share

This function looks like `ftp`.

`fileshare` include keywords `port` and `path`.

eg: 

```
{
	"fileshare": [
		{"port": "9991", "path": "/home/lz"}
	]
}
```
















