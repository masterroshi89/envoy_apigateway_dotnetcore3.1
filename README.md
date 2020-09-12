# Envoy_ApiGateway_dotnetcore3.1

.

#dotnet core project created with envoy API gateway


#create dotnet project
dotnet new webapi -n CoffeeAPI

#Run the project
dotnet run

#Generate dev certs
dotnet dev-certs https: -ep $env:USERPROFILE\.aspnet\https\CoffeeAPI.pfx -p Srishti@2019

#add trust certs
dotnet dev-certs https --trust

#Certs Location
C:\Users\<user_name>\.aspnet\https

#Add "<userSecretsId>" to csproj file.

#Add kestrel certs to projects
dotnet user-secrets set "kestrel:Certificates:Development:Password" "Srishti@2019"

#location of UserSecrets file
C:\Users\gurpreet.singh\AppData\Roaming\Microsoft\UserSecrets

#build envoy
go > envoy folder
docker build -t envoygateway .

#run envoygateway and map port
docker run -p 9901:9901 -p 10000:10000 envoygateway

#from WSL
explorer.exe .
Copy the htts config file

#execute the command
openssl req -config https.config -new -out csr.pem

#generate certificate from key.pem generated from previous commands
openssl x509 -req -days365 -extfile https.config -extensions v3_req -in csr.pem -signkey key.pem -out https.crt
