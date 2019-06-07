FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /src
RUN dotnet restore "SGL_API_DescargaAndroid.csproj"
COPY . .
WORKDIR "/src/SGL_API_DescargaAndroid"
RUN dotnet build "SGL_API_DescargaAndroid.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "SGL_API_DescargaAndroid.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "SGL_API_DescargaAndroid.dll"]