# Configurações variáveis de ambiente

1. Executar 
   1. code ~/.zshrc

# Configurações

```.zshrc
export ANDROID_HOME=~/sdk/android/sdk
export PATH="$PATH:$ANDROID_HOME/tools"
export PATH="$PATH:$ANDROID_HOME/platform-tools"

export PATH=~/sdk/flutter/bin:$PATH
export PATH=~/sdk/flutter/bin/cache/dart-sdk/bin:$PATH
```