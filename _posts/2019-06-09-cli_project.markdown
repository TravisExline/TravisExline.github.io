---
layout: post
title:      "CLI Project"
date:       2019-06-09 09:22:42 -0400
permalink:  cli_project
---


Where to even begin on this one?  Needless to say, my first project was daunting, rewarding, and difficult. Let's dive in.

### What does it do?

I created a CLI that would inspect 10 different high powered computers from the end of 2018 to early 2019.  All the data for these computers was scraped off of the Tech Radar website below:

https://www.techradar.com/news/computing/pc/10-of-the-best-gaming-pcs-you-can-buy-in-2015-1304263

Scraping in and of itself is a daunting task, and probably one of the most difficult aspects of my CLI.  

### The Great Es-Scrape

Initially, I was really confident when it came to scraping.  From previous practice, it didn't really seem any different than meticulously sweeping through a long list and just recreating an order of classes, IDs, or text.  I quickly realized that, although it is just reiterating a set order, it was much more specific and rule based. 

Unfortuneatly for me, I ran into issues.  Scraping a title, the names of computers, and a large block of specs wasn't a huge problem. However, when I wanted to break those specs down individually, it became more daunting.  Although I could have simply put a large block of computer specs next to each computer, I opted for a cleaner look, with iterating through this larger block of code and singling out each individual spec for each computer,  Check out my code below:

```

require 'open-uri'

WEB_COMPUTERS = "https://techradar.com/news/computing/pc/10-of-the-best-gaming-pcs-you-can-buy-in-2015-1304263";

class Computers::Scraper;

  def self.scrape;
  doc = open(WEB_COMPUTERS);
  parsed_doc = Nokogiri::HTML(doc);
  computer_name = parsed_doc.css("h3");
  computer_details = parsed_doc.css(".news-article");
  computer_name.each do |pc_name, cpu, graphics, ram, storage, brand|;
    pc_specs = computer_details.css(".specs__container");
    cpu = pc_specs.text.split(" | ")[0];
    graphics = pc_specs.text.split(" | ")[1];
    ram = pc_specs.text.split(" | ")[2];
    storage = pc_specs.text.split(" | ")[3];
    brand = pc_name.text.split(" ")[1];
    Computers::PCs.new(pc_name.text, cpu, graphics, ram, storage, brand);
  end;
end;
end;

#computer_details = parsed_doc.css(".specs__container");
#computer_details.text.split(" | ");
#specs  => parsed_doc.css("p.specs__container").first.text;
#parsed_doc.css("strong") => STATS KEY!!!!!!;

```

### The CLI Itself

As for the CLI itself, I created a simple, easy to use, CLI.  I wanted to keep everything easy, with initially returning a list of computers to choose from, an option to see these computers specifically, or to see a list of brands.  I ran into some trouble when scraping the brand name from the website. 

```
  def self.scrape_brand;
    computer_array = [];
    doc = open(WEB_COMPUTERS);
    parsed_doc = Nokogiri::HTML(doc);
    computer_name = parsed_doc.css("h3");
    computer_name.each do |pc|;
      computer_array << pc.text.split(". ")[1];
    end;
    computer_array.pop;
    computer_array.each do |computer|;
      @@all << computer.split(" ")[0];
    end;
  end;	
	```
	
	At first, I was repeatedly getting NoMethodErrors for my .split.  
	
	*Spongebob Narrator Voice Here* Two hours later.
	
	As it turns out, I had a nil value at the end of my computer_array. A simple .pop did the trick, and I was able to get the brand names into an array.
	
	### Conclusion
	
	I know my code isn't perfect, so please, it anyone happens to look at this, let me know how I might be able to tweak this, make improvments, and give me some feedback!
	
	One mediocre CLI, a small mental breakdown, and a hours spent staring at the same few lines of code later, I feel acomplished.  Even though I know theres a lot of mistakes, a lot of code that could be wirtten cleaner and better, and even parts of my code that aren't 100% how I want them, it feels good to actually accomplish something that came from absolutely nothing. 
	
	




