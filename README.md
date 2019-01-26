
# PHPデバッグ環境構築
## Docker側
プロジェクトトップに.envを作成し、ドキュメントルートを設定
``` 
DOCUMENT_ROOT=./www/html
```

動かすだけなら、.env-dummyを.envにリネームする  
「docker-compose up -d」する

## Visual Studio Code側
拡張機能から、「PHP Debug」をインストール  
左の虫アイコン > 左上の歯車でlaunch.jsonを開きConfigurationsに以下を追加  

```
    "configurations": [
        {
            "name": "Listen for XDebug",
            "type": "php",
            "request": "launch",
            "port": 9000, // php.iniで設定したポート
            "pathMappings": {
                // {docker上のdocument root}:{ローカルのdocument root}
                "/var/www/html":"/Users/xxxxx/dev/projects/php-apache-postgre/www/html"
            }
        }
```