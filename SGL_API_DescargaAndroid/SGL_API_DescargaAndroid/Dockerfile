FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /app
COPY *.csproj ./
RUN dotnet restore SGL_API_DescargaAndroid.csproj
COPY . ./
RUN dotnet publish SGL_API_DescargaAndroid.csproj -c Release -o out
FROM microsoft/dotnet:2.1-aspnetcore-runtime AS runtime
WORKDIR /app
COPY --from=build /app/out .
EXPOSE 80
EXPOSE 443
ENTRYPOINT ["dotnet", "SGL_API_DescargaAndroid.dll"]