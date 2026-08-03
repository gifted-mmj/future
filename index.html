$ErrorActionPreference = "Stop"
$root = Split-Path -Parent $MyInvocation.MyCommand.Path
$prefix = "http://localhost:8000/"
$listener = New-Object System.Net.HttpListener
$listener.Prefixes.Add($prefix)

try {
  $listener.Start()
} catch {
  Write-Host "PORT_IN_USE"
  exit 1
}

Write-Host "SERVING $prefix from $root"

while ($listener.IsListening) {
  $context = $listener.GetContext()
  $requestPath = $context.Request.Url.AbsolutePath.TrimStart("/")
  if ([string]::IsNullOrWhiteSpace($requestPath)) { $requestPath = "index.html" }
  $filePath = Join-Path $root $requestPath
  if (Test-Path $filePath -PathType Leaf) {
    $bytes = [System.IO.File]::ReadAllBytes($filePath)
    $response = $context.Response
    switch ([System.IO.Path]::GetExtension($filePath).ToLowerInvariant()) {
      ".html" { $response.ContentType = "text/html; charset=utf-8" }
      ".js"   { $response.ContentType = "application/javascript; charset=utf-8" }
      ".css"  { $response.ContentType = "text/css; charset=utf-8" }
      ".json" { $response.ContentType = "application/json; charset=utf-8" }
      ".png"  { $response.ContentType = "image/png" }
      ".jpg"  { $response.ContentType = "image/jpeg" }
      ".jpeg" { $response.ContentType = "image/jpeg" }
      ".svg"  { $response.ContentType = "image/svg+xml" }
      default { $response.ContentType = "application/octet-stream" }
    }
    $response.ContentLength64 = $bytes.Length
    $response.OutputStream.Write($bytes, 0, $bytes.Length)
    $response.OutputStream.Close()
  } else {
    $response = $context.Response
    $response.StatusCode = 404
    $buffer = [System.Text.Encoding]::UTF8.GetBytes("404 Not Found")
    $response.ContentType = "text/plain; charset=utf-8"
    $response.ContentLength64 = $buffer.Length
    $response.OutputStream.Write($buffer, 0, $buffer.Length)
    $response.OutputStream.Close()
  }
}
