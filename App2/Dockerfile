FROM microsoft/aspnetcore-build AS build-env

#FROM microsoft/dotnet:sdk AS build-env

WORKDIR /app
COPY *.csproj ./
RUN dotnet restore 
COPY . ./

RUN dotnet publish -c release -o output


FROM microsoft/aspnetcore 

#FROM microsoft/dotnet:aspnetcore-runtime

COPY --from=build-env /app/output .

EXPOSE 5001

ENV ASPNETCORE_URLS=http://*:5001

ENTRYPOINT ["dotnet","app2.dll"] 
  
