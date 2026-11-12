# SupportIQ

SupportIQ is an AI-powered customer support knowledge portal.

## Project structure

- `src\backend\SupportIQ.Api` — .NET 10 ASP.NET Core API.
- `src\frontend\SupportIQ.Web` — React + TypeScript frontend using Vite and Bootstrap.
- `SupportIQ.sln` — backend solution.

## Run locally

Start the API:

```powershell
dotnet run --project src\backend\SupportIQ.Api
```

The API health endpoint is available at `http://localhost:5112/health` when using the `http` launch profile.

Start the frontend in a separate terminal:

```powershell
Set-Location src\frontend\SupportIQ.Web
npm install
npm run dev
```

## Build and lint

```powershell
dotnet build SupportIQ.sln
Set-Location src\frontend\SupportIQ.Web
npm run build
npm run lint
```
