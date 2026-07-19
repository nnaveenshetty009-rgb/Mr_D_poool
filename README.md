import tempfile, os
from zipfile import ZipFile
tmp=tempfile.mkdtemp(dir="/mnt/data")
for name,content in {
"index.html":"<!DOCTYPE html><html><head><meta charset='UTF-8'><title>Mr_D_poool</title><link rel='stylesheet' href='style.css'></head><body><h1>Mr_D_poool</h1><p>The Best Movie Trailers & Recaps</p><button>Watch Latest Trailer</button><script src='script.js'></script></body></html>",
"style.css":"body{background:#111;color:#fff;font-family:Arial;text-align:center;padding:40px}button{padding:10px 20px}",
"script.js":"console.log('loaded');"
}.items():
    open(os.path.join(tmp,name),"w").write(content)
zip_path="/mnt/data/Mr_D_poool_Website_New.zip"
with ZipFile(zip_path,"w") as z:
    for f in os.listdir(tmp):
        z.write(os.path.join(tmp,f),f)
print(zip_path)
