# PowerShell file for FTP communication

# Input data from the core file and the plain text(s)
$server = $args[1]
$user = $args[2]
$pass = $args[3]
$script = $args[4]


if ($script -eq 1)
{
	$file_location = "C:\Users\user\Desktop\Hybrid-automation\certificate1.auto.rsc"
	$file = "certificate1.auto.rsc"
}

elseif ($script -eq 0)
{
	$file_location = "C:\Users\user\Desktop\Hybrid-automation\certificate2.auto.rsc"
	$file = "certificate2.auto.rsc"
}

$ftpurl = "ftp://${user}:${pass}@${server}/${file}"

$webclient = New-Object System.Net.WebClient
$uri = New-Object System.Uri($ftpurl)
# Write-Output "${uri}"

try {
		$webclient.UploadFile($uri, $file_location)
		Write-Output "`>>> The script has been uploaded to the router" 
	}

catch {
			Write-Output "`>>> Script cannt be uploaded >> The user or pass are wrong or FTP is not enable !"
			$error = "The user or pass are wrong for server: ${server}"
			$exception = $_.Exception.Message
			Out-File -FilePath .\errors.txt -Append -InputObject $exception -Encoding utf8
			Out-File -FilePath .\errors.txt -Append -InputObject $error -Encoding utf8
	}
