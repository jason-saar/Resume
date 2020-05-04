        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult Create([Bind(Include = "PhotoId,PhotoFile,OriginalHeight,OriginalWidth,Title")] Photo photo, HttpPostedFileBase file)
        {
            if (ModelState.IsValid)
            {
                byte[] photoArray = ImageBytes(file);
                photo.PhotoFile = photoArray;
                Bitmap img = new Bitmap(file.InputStream);
                photo.OriginalHeight = img.Height;
                photo.OriginalWidth = img.Width;

                db.Photo.Add(photo);
                db.SaveChanges();

                return RedirectToAction("Index");
            }

            return View(photo);
        }