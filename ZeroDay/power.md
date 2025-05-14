Description: The password to the zip file is infected, this is a real-life-like PowerShell deobfuscation challenge, so it’s recommended to run it in a VM.


we got a powershell script command named update.ps  we have some obfuscated powershell script 

```(neW-oBject  SystEm.iO.comprESsiOn.DeflateSTREaM( [Io.mEMOrYSTReaM] [CONVeRt]::frOmBAse64sTrIng( 'ZU9dS8MwFH0f7D8cRh86dO3wQbrCQAX1QUHYVhDEhyS9tQWXlDSFFtl/96a1Y2C45OPcez4SlNTtna30F7ZYCAW5hryBFBCbYc8hbuFxAakgBsTjBSR53FfiWR6XIALlIDUUX2gxnwWdsS/Us8G6ywt+16JxJCud2W/vWjpXN2kcT3CkzDF+zfbJRu/umY/5rGi1cpXReH/brca8YVDpunUPvaPmGn8eS/zwPK/AtG7qssdduBzxwlgSqkQYSG6h0riQObP/KVxtMRJWko0mt3H4NB6WXGs1PvY9/+IYHahz0aNWJuesn2maHZ6S6JncFP5CnaOdfgE=' ),[Io.COmPREsSION.COmPreSsioNMoDe]::DECOmpreSs )| foreaCH {neW-oBject  SYsTem.io.sTREaMrEADer($_ , [TeXt.EnCodinG]::ASciI )} |fOreACH {$_.ReaDToENd( ) }) |. ( $pSHoMe[4]+$PsHOmE[34]+'x')```

we need to deobfuscated this script  by decoder base64 and decompressed the memory stream and then here is the deofuscated method  : 
```# Save the base64 string to a variable
$base64 = 'ZU9dS8MwFH0f7D8cRh86dO3wQbrCQAX1QUHYVhDEhyS9tQWXlDSFFtl/96a1Y2C45OPcez4SlNTtna30F7ZYCAW5hryBFBCbYc8hbuFxAakgBsTjBSR53FfiWR6XIALlIDUUX2gxnwWdsS/Us8G6ywt+16JxJCud2W/vWjpXN2kcT3CkzDF+zfbJRu/umY/5rGi1cpXReH/brca8YVDpunUPvaPmGn8eS/zwPK/AtG7qssdduBzxwlgSqkQYSG6h0riQObP/KVxtMRJWko0mt3H4NB6WXGs1PvY9/+IYHahz0aNWJuesn2maHZ6S6JncFP5CnaOdfgE='

# Decode and decompress
$bytes = [Convert]::FromBase64String($base64)
$ms = New-Object System.IO.MemoryStream(,$bytes)
$ds = New-Object System.IO.Compression.DeflateStream($ms, [IO.Compression.CompressionMode]::Decompress)
$sr = New-Object System.IO.StreamReader($ds, [Text.Encoding]::ASCII)
$decompressed = $sr.ReadToEnd()

# Print the decompressed code (do NOT use Invoke-Expression!)
$decompressed
```

after the deofuscated you can see some hex value and code alanzyer the code 

code  : 
```
$hexString = "ac b0 b2 ba a9 ba ad a6 ac ba bc aa ad ba af be ac ac a8 b0 ad bb ee ed ec ec ed ee"
$xorKey = 0xdf
$pastebinUrl = "https://pastebin.com/LUS89nRA"
 
function XOR-String($inputBytes, $xorKey) {
    $outputBytes = @()
    foreach ($byte in $inputBytes) {
        $outputBytes += $byte -bxor $xorKey
    }
    return [System.Text.Encoding]::UTF8.GetString($outputBytes)
}
```
when are decrypted  the hex strings you will get the password is : ```someverysecurepassword123321``` in the url of the script indenta the as pastbin.com :A pastebin is an online service that allows users to store and share plain text.

then you get the flag 

Flag  : ZeroDays{powershell_de0bfuscation!}

