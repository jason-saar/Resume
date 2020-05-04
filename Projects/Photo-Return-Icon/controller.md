		[AllowAnonymous]
        public ActionResult DisplayPhoto(int? id) //nullable int
        {            
            string filePath = Server.MapPath(Url.Content("~/Content/Images/no-image.png"));
            Image noImageAvail = Image.FromFile(filePath);
            var converter = new ImageConverter();
            var byteData = (byte[])converter.ConvertTo(noImageAvail, typeof(byte[]));
            if (id.HasValue)
            {                
            Photo photo = db.Photo.Find(id);
                if (photo == null)
                {
                    return File(byteData, "image/png");
                }
                else
                {
                    return File(photo.PhotoFile, "image/png");
                }                                                                  
            }
            else
            { 
                return File(byteData, "image/png");
            }
        }