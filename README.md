# go-demo 

## init with gin

```
# Create dir
mkdir -p /Users/hosea/work/go-modules/go-demo
cd /Users/hosea/work/go-modules/go-demo

# Initialize git repo
echo "# go-demo" >> README.md
git init
git add README.md
git commit -m "go init"
git remote add origin git@github.com:hoseadevops/go-demo.git
git push -u origin master

# Initialize a new module:
go mod init github.com/hoseadevops/go-demo

# Hello world
cat <<EOF > hello.go
package main

import "github.com/gin-gonic/gin"

func main() {
	r := gin.Default()
	r.GET("/ping", func(c *gin.Context) {
		c.JSON(200, gin.H{
			"message": "pong",
		})
	})
	r.Run() // listen and serve on 0.0.0.0:8080
}
EOF

# Optional step to create a vendor directory
go mod vendor

# Start vs-code and watch some changes
code . 

# Run hello.go and visit 0.0.0.0:8080/ping on browser
go run hello.go

# Build && run 
build -o hello
./hello
```


