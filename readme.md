## 來源
<https://ithelp.ithome.com.tw/users/20031776/ironman/1022>

### 安裝 ansible

```
sudo pip3 install ansible
```

測試

```shell
ansible all -m command -a "echo Hello World"
```

噴錯

```text
to use the 'ssh' connection type with passwords or pkcs11_provider, you must install the sshpass program
```

- 建立需要的檔案

```shell
vim sshpass.rb

require 'formula'

class Sshpass < Formula
  url 'http://sourceforge.net/projects/sshpass/files/sshpass/1.06/sshpass-1.06.tar.gz'
  homepage 'http://sourceforge.net/projects/sshpass'
  sha256 'c6324fcee608b99a58f9870157dfa754837f8c48be3df0f5e2f3accf145dee60'

  def install
    system "./configure", "--disable-debug", "--disable-dependency-tracking",
                          "--prefix=#{prefix}"
    system "make install"
  end

  def test
    system "sshpass"
  end
end
```

- 安裝 sshpass

```shell
brew install sshpass.rb
```
