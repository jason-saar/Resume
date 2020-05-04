		public ActionResult Index()
        {
            var productions = from p in db.Productions
                          select p;


            //Filter list by current and future productions
            var query = productions.Where(p => p.OpeningDay > DateTime.Now || p.IsCurrent == true || (p.OpeningDay <= DateTime.Now && p.ClosingDay >= DateTime.Now))
                .OrderBy(p => p.OpeningDay);

            List<Production> unorderedProductions = query.ToList();
            var orderedProductions = SortProductions(unorderedProductions);

            return View(orderedProductions);
        }

        private List<Production> SortProductions(List<Production> list)
        {
            var sorted = new List<Production>();
            var onStage = new List<Production>();
            var current = new List<Production>();
            var comingSoon = new List<Production>();

            foreach (var item in list)
            {
                if (item.OpeningDay <= DateTime.Now && item.ClosingDay >= DateTime.Now)
                {
                    onStage.Add(item);
                }
            }
            sorted.AddRange(onStage);
            foreach (var item in list)
            {
                if (item.IsCurrent && !sorted.Contains(item))
                {
                    current.Add(item);
                }
            }
            sorted.AddRange(current);
            foreach (var item in list)
            {
                if (item.OpeningDay > DateTime.Now && !sorted.Contains(item))
                {
                    comingSoon.Add(item);
                }
            }
            sorted.AddRange(comingSoon);

            return sorted;
        }