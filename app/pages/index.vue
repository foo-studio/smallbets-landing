<template>
  <div class="w-screen h-screen bg-fall-50">
    <UContainer>
      <div class="flex py-4 items-center gap-2">
        <NuxtImg class="rounded-lg h-8" src="/logo.jpg" />
        <span class="font-serif">Small Bets</span>
      </div>
    </UContainer>
  </div>
</template>

<script setup>
definePageMeta({
  colorMode: "light",
});

const showMoreTestimonials = ref(false);

const courses = [
  "Building a Media Business - Arvid Kahl",
  "Intro to Internet Pipes - Steph Smith",
  "Understanding LinkedIn - Justin Welsh",
  "Publish a Best-Selling Course on Udemy - Hassan Osman",
  "Amazon KDP Crash Course - Greg Lim",
  "Effortless Screencasting - Aaron Francis",
  "Domain-First Development - Peter Askew",
  "Delve Into Expiring Domain Names - Peter Askew",
  "Building Businesses on Wordpress - Peter Askew",
  "Spreading Ideas with Memes - Dagobert Renouf",
  "Understanding the X Algorithm - Dagobert Renouf",
  "Emerging from the Void on X - Daniel Vassallo",
  "Make $500 on Upwork by Monday - Sean O'Dowd",
  "Enough GPT to be Dangerous - Sairam Sundaresan",
  "AI for the Rest of Us - Sairam Sundaresan",
  "Growing on Substack - Elle Griffin",
  "Getting Started on YouTube - Aprilynne Alter",
  "Casual YouTube Creation - Azul Wells",
  "Marketing Fundamentals for Non-Marketers - Daniel Vassallo",
  "Fundamentals of Internet Marketing - Amanda Natividad",
  "Gumroad Crash Course - Daniel Vassallo",
  "The Art of Podcasting - Espree Devora",
  "Explaining Ideas Visually - Janis Ozolins",
  "Intro to SEO - Jordan O'Connor",
  "SEO Keyword Research - Jordan O'Connor",
  "Building a Content Roadmap for SEO - Jordan O'Connor",
  "Wandering the Pathless Path - Paul Millerd",
  "Building & Launching macOS Apps with SwiftUI - Grace Huang",
  "Intro to Google Ads - Jay Mac",
  "Extremely Minimum Viable Video - Cam Houser",
  "Build in Public on Twitch - Charlie Coppinger",
  "What to Expect When You Go Self-Employed - Catherine Cusick",
  "A Practical Guide to Self-Employment Taxes - Catherine Cusick",
  "Getting Started with Short-Term Rentals - Isaac French",
  "Creating Income through Real Estate - Louie Bacaj",
  "A Quick Start Guide to Adult ADHD - Jesse Anderson",
  "Getting The Attention of Influential People - Benjamin Carlson",
  "Getting Featured in the Media - Benjamin Carlson",
  "Getting Started with Midjourney - Christian Heidorn",
  "The Basics of Buying & Selling Businesses - Thomas Smale",
  "Art of Interviewing - Danny Miranda",
  "Self-Sponsor Your Own US Green Card - Archie Agrawal",
  "Crowdfunding Crash Course - Tugra Sahiner",
  "State of the Creator Economy - Sahil Lavingia",
  "Equity Crowdfunding for Solopreneurs - Sahil Lavingia",
  "Notion for Creators and Entrepreneurs - Monica Lim",
  "A Stoic Guide to Dealing with Uncertainty - Mahmoud Rasmi",
  "A Pragmatic Guide to Business Ethics - Mahmoud Rasmi",
  "Reproducible Success Strategies and Ergodicity - Luca Dellanna",
  "Small Bets Fundamentals - Daniel Vassallo",
];

const testimonials = [
  "Arvid Kahl: \"This isn't just an **amazing community** for eager founders to learn in; it's also an expression of Daniel's expansive teaching mindset. Allowing people to teach themselves by re-living your past lectures is an active act of empowering those who already have an overflowing schedule.\"",
  'Florin Pop: "There are **tons of webinars with amazing people**, and the community is full of amazing people."',
  'Tony Dinh: "Small Bets is **the most active server** on my Discord!"',
  'Espree Devora: "Small Bets is the most high value engaged helpful business community on the internet. We pay a one time small fee for life time access to **quality connections and impactful education that transforms** our lives."',
  'Kenny Liu: "I just finished the Small Bets lecture about Upwork with @SeanODowd15. **Countless gems for takeaway!** @dvassallo and his team continue to provide real value for the Small Bets community. So glad I signed up!"',
  'Ergest Xheblati: "Honestly the best community I\'ve been a part of in the last 10 years"',
  'Aprilynne Alter: "I can easily say that the Small Bets community has been **one of the most engaged groups of people** I\'ve had the pleasure of teaching! Great community there."',
  'Hassan Osman: "This course by @dvassallo will show you: How to think about starting a business; How to reduce the risk of failure; How to use randomness to your advantage. **Truly one of the best courses I\'ve taken**."',
  'Dan Rowden: "The Discord is **full of amazing makers**. It\'s like a curated group of the best from Twitter, plus more interaction and value."',
  'Vic Vijayakumar: "You get an active community Discord, lots of guest lectures (with recordings), tons of freebies (and/or discounts to various saas / ebooks / courses), and in my case I also **made some very good friends**."',
  "Monica Lim: \"You don't need another course but this by @dvassallo legit freed me from self-sabotage and procrastination. It's **value dense**, affordable and the community is still small and quite active.\"",
  'Manny de Souza: "By far, the best content I consumed about entrepreneurship and lifestyle. It is amazing to be **among of so many like minded people**."',
  'Jeffrey Guenther: "**Absolutely worth the price** of admission. It\'s like having access to a bunch of paid courses."',
  "Ankur Tyagi: \"If you're looking for an awesome community. If you're trying small bets and need **genuine feedback**. If you need to understand how randomness played a big role in your life. This is for you.\"",
  'Jeremy Smith: "Daniel is solidifying many concepts I had some intuition/pattern matching for, but couldn\'t yet articulate. **Highly recommended**!"',
  'George McEntegart: "A community that **keeps giving value again and again**."',
  'Ankita Kulkarni: "**Highly recommend it**, you start thinking in small bets vs taking on huge projects which cost you time and money!"',
  'Rafael Rinaldi: "This community truly is **the gift that keeps on giving**."',
  'Jordan Davis: "Very few one-time purchases continue to add more and **more value over time** like this."',
  'Brock Briggs: "The community is **absolutely invaluable**."',
  'Brandon Fearing: "Joined @dvassallo small bets community yesterday and the guest lecture recordings are 100%. Found @searchbound\'s domain first development **super intriguing**. Maybe now I can put my 40+ unused domains to use!"',
  'Hugo Hamel: "It is so **refreshing and inspiring** to be part of the Small Bets community. It might be bad for the economy, but it\'s extremely healing in many ways to experience. Truly a beautiful community!"',
  'Nick Hammond: "Love being able to go back into the recordings on my own time. Appreciate **all of the info you\'ve collected in one place**!"',
  'Angad Singi: "Being a part of smallbets.co, I love the community. The instant feedback, **quality conversations**, and exploring possibilities of digital business is superb."',
  'Corey Wilks: "Shared the same wins in a few communities recently. **Nothing beats the supportiveness** of the Small Bets community."',
  'Shivam Dewan: "smallbets.co is my **new idea generator**. If you need inspiration and a supportive community, this is the place to be. Been into so many discord groups but only this one I actually participate in."',
  'Travis Hayes: "Highly recommend looking into Daniel\'s small bets community. As a new active twitter user, I often have a ton of questions. **The community is engaged** and has been helpful."',
  'Miche Priest: "Taking this course and joining this Discord has been an incredible learning journey. Top notch, creative, generous, engaged people coming together to figure out how to design work around life. **Makings solopreneurship not so solo**."',
  "Enrique Benitez: \"Just finished this course by @dvassallo and it's by far **the best course I've ever taken**, Daniel explains and dissects the process of building a portfolio of small bets thoroughly, from product ideas, randomness and luck, making money and lifestyle design.\"",
  'Jason Akinaka: "**Highly recommend** it for those who, like me, dread the 9-5 and have way too many interests to ever want to go back."',
  "Takamichi Okubo: \"Just finished @dvassallo's awesome cohort course. It's 9+ hours of **pure informativeness and inspiration**.\"",
  'Gaurav Singh: "For a decade, I was on a set life path. Then I decided to change it all and start from scratch. This was hard. For many months, I was lost. Till I did @dvassallo\'s Small Bets course. It was one of the most **transformative experiences of my life**."',
  "Trevor O'Hara: \"Proud to say I'm a graduate of the very first cohort! **Definitely worth it**.\"",
  'Andreas Lehr: "I joined the Small Bets course by @dvassallo in April and can highly recommend it. The content is really great and inspiring. The outstanding part is the Discord community which is very active --- you get **lots if inspiration** just by consuming the participants content alone."',
  'Aaron Batilo: "Just launched my first small bet after being in this community. The lessons learned gave me **much more confidence** about taking risks and investing my time."',
  'Haifa Altwaijry: "The gift that keeps on giving. **You\'ll never regret signing up**!"',
  'Daniel Rojas: "This is **an awesome community**, I came because of the course, stayed thanks to the community."',
  'Alex Konewko: "So refreshing to hear such **authentic and insightful content** being shared with an interesting and diverse cohort. Highly recommended!"',
  'Vineet Thanedar: "There is **no better community of solopreneurs** on the internet."',
  'Mike Ying: "**Great quality classes**."',
  'Mark Willis Borum: "**Worth 10x the cost**."',
  'Lila Tace: "Small Bets is magical. **I found my place**."',
  'Nick Groeneveld: "Can highly recommend Small Bets. It is **the best investment in my career** I made. Connected with great people. Joined insightful master classes. Made over 8x the entrance fee on new projects."',
  'David Nix: "If you are even a teeny-tiny bit interested in entrepreneurship, **you need this**."',
  "Alberto Sadde: \"**One of the best communities** I'm part of. The events are top notch and even if I'm often unable to join the live session, recordings are always available.\"",
  'Paul Waweru: "**Best investment I\'ve made**!"',
  'Dave Kang: "This is the most interesting entrepreneurial community I\'m part of, **smart people** making a living off the corporate grid."',
  "Milly Barker: \"Watching just 6 hours of @dvassallo's Small Bets Fundamentals Zoom recordings has done me more good than 3+ years of striving to figure things out myself. **Gratitude doesn't even come close**.\"",
  'Denis Loginoff: "Went to a potentially **life-changing** lecture by @LBacaj in Small Bets! It made me rethink my entire strategy on side income."',
  'Matouš Jemelka: "Insane February line-up of events at @SmallBetsDotCom. Wonderful guests riffing on fascinating topics. I am especially looking forward to @jdnoc and @stephsmithio, but the overall **bar is extremely high**."',
  'Anton Cherkasov: "I joined Small Bets last week, although I haven\'t had much time to explore. Nevertheless, through just a few chats, I have already gained valuable insights. The community of amazing people is **truly incredible**."',
  'Venkatesh Narayanan: "Worth joining small bets and try out new things. The guest lectures **recordings are fantastic**."',
  'Kunal Modi: "Thanks to @dvassallo\'s small bets course and its **amazing community**, I got the jumpstart that would have otherwise taken me ages to figure out on my own."',
  'Greg Gilbert: "I rarely recommend products publicly, but the Small Bets community offers **incredible value for the price**."',
];

const formatTestimonial = (text) => {
  return text.replace(/\*\*(.*?)\*\*/g, '<span class="highlight">$1</span>');
};
</script>
