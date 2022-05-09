<pre>
#判断ua是 Destop 环境 还是 Mobile 环境
ua = req.headers[ 'user-agent' ]
if ua.search( /iPod/    )    is -1 and 
   ua.search( /iPhone/  )    is -1 and 
   ua.search( /iPad/    )    is -1 and 
   ua.search( /Kindle/  )    is -1 and 
   ua.search( /Android/ )    is -1 and 
   ua.search( /Opera Mini/ ) is -1 and 
   ua.search( /BlackBerry/ ) is -1 and 
   ua.search( /webOS/      ) is -1 and 
   ua.search( /UCWEB/      ) is -1 and 
   ua.search( /Blazer/     ) is -1 and 
   ua.search( /PSP/        ) is -1 and 
   ua.search( /IEMobile/   ) is -1 
then osdesktopdesktop' else os = 'mobile'

#print os
console.log 'os = osos

</pre>