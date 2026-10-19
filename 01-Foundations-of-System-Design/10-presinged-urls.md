Pre signed URLs

It powers huge platform like youtube, dropbox and netflix.

Have you ever imagined how you can upload a massive video file to the youtube without their servers exploding.

Thats where the pre signed URLs comes into the play.

Imagine millions of people uploading videos at the same time.

If all of those files had to flow throug the application servers, those servers would becomd a massive bottleneck.

presinged urls solves this problem in real elequent way

Let's thing about the tradition way of uploading the files.

the video goes to the application server the server authenticates you checks permissions and then forward your video to the cloud storage.

if the 1000s of user upload simultaneously the server bandwidth would get crushed and double transfer

user to server, then server to storage.

 we need a way for a user to directly upload to cloud storage. thats excatly what a pre-singed URLs do.

 A persinged URL is essentially a temporary, secure key to perform one specific action on the cloud storage, think of it like a hotel room key card.

 and it expires automatically after a set time.

 let me walk you through when you upload a video to the youtube.

 you click on the upload button, the browser sends the request to the server "Hey i want to upload a video" then the youtube server authenticates you and check permissions and request a pre-singed URL from cloud storage. and it says to the cloud storage, generate a pre singed url to upload a video for this user make it valid for the next 15 minutes then the cloud storage generates a special URL, 


 This URL has few encoded things in it.

 The location where the file would be stored.
 The HTTP method that is allowed.
 The Time to expire
 and most importantly the cryptographically signature.

 the youtube server receives this pre signed url and send back to the user.

 the browser upload the video directly to that url.

 when the cloud storage receives your request, it validates the url and check the signature, has it expired, is the http method correct.

 the cloud storage sends response that video is uploaded successfully either to your browser or the youtube server.

 lets talk about how it is actually secured, if anyone has that URL, can't they upload whatever they want?

 The answes in no, the URl contains a cryptographic signature.

 when the could storage generates the URL it takes several pieces of the information.

 the file path, the http method, expiration time and any other parameters.

 then hashes it with a cryptographic hash funcion along with the secret key, this produces a signature that is appended to the URL

if someone try to upload with the URL, it takes all the parameters and goes all the steps and check if the result matches the signature in the URL.


The presinged URL is the perfect example of separating your data plane vs control plane 


Your application server handles the control plane the authentication authrization meta data, url generation.

Data Plane: (video file, images, document, direct to storage) The acctuall data, goes directly from client to storage.


when to use this patteren anythime when you're working with large files, downloads videos, documents, datasets.

you need to handle edge cases.

 - what if the upload fails halfway.
 - what if user request URL but never uploads.
 - what about very large files > 100GB


 you might need a cleanup job to handle the abandon uploads.
