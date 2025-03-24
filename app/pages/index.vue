<template>
  <div class="min-h-screen bg-cod-50 overflow-x-hidden">
    <!-- Navigation Bar -->
    <header>
      <UContainer>
        <div class="flex py-4 items-center justify-between">
          <div class="flex items-center gap-2">
            <img class="rounded-lg h-8" src="/logo.jpg" />
            <span class="font-logo text-xl font-bold">Small Bets</span>
          </div>
          <UButton
            size="xl"
            class="px-0 hover:underline"
            :to="signIn"
            variant="link"
            >Sign In</UButton
          >
        </div>
      </UContainer>
    </header>

    <!-- Hero Section -->
    <section class="py-16 md:py-24">
      <UContainer>
        <h1
          class="text-4xl md:text-5xl xl:text-7xl uppercase font-serif font-medium mb-6 text-black"
        >
          Start Small
        </h1>
        <div
          class="text-xl md:text-2xl lg:text-3xl mb-8 text-black leading-relaxed space-y-4"
        >
          <p>Forget about "starting a company."</p>
          <p>Try making $1,000 with a small project first.</p>
          <p>
            When you join Small Bets you'll find a support network ready to help
            you get your first small wins.
          </p>
        </div>
        <UButton
          :to="joinNow"
          size="xl"
          class="hover:ring-3 hover:ring-primary-950 hover:bg-primary-500 uppercase font-bold text-lg px-8"
          >Join Now</UButton
        >
      </UContainer>
    </section>

    <div class="h-12 bg-transparent relative">
      <div
        class="h-25 w-[120vw] bg-secondary-50 -left-20 top-0 border-t border-secondary-200 absolute -rotate-3"
      ></div>
    </div>

    <!-- Testimonials -->
    <section class="pt-20 pb-40 bg-secondary-50">
      <UContainer class="relative">
        <h2 class="section-title">What Our Members Say</h2>
        <div
          :class="[
            showAllTestimonials
              ? 'max-h-[8000px] md:max-h-[6000px] lg:max-h-[4000px]'
              : 'max-h-[1200px] md:max-h-[1000px] lg:max-h-[800px]',
            'overflow-hidden transition-[max-height] duration-500',
          ]"
        >
          <div class="md:columns-2 lg:columns-3 gap-14 space-y-8">
            <div
              v-for="(testimonial, index) in testimonials"
              :key="index"
              class="break-inside-avoid space-y-2 py-4"
            >
              <p
                class="font-medium text-lg md:text-2xl"
                v-html="formatTestimonial(testimonial.quote)"
              ></p>
              <p class="text-gray-700 font-bold text-lg">
                — {{ testimonial.name }}
              </p>
            </div>
          </div>
        </div>

        <div
          v-if="!showAllTestimonials"
          :class="[
            'mt-8 text-center w-full py-4',
            !showAllTestimonials &&
              '-bottom-10 h-30 left-0 z-10 absolute bg-white/2 backdrop-blur-xs',
          ]"
        >
          <UButton
            variant="subtle"
            size="lg"
            class="bg-primary-100/80 hover:bg-primary-100/70 hover:ring-2 cursor-pointer font-medium px-6"
            @click="toggleShowAllTestimonials"
          >
            {{
              showAllTestimonials
                ? "Show Less Testimonials"
                : "Show More Testimonials"
            }}
          </UButton>
        </div>
      </UContainer>
    </section>

    <!-- <div class="h-12 bg-transparent relative"> -->
    <!--   <div -->
    <!--     class="h-26 w-[110vw] bg-cod-50 -left-10 -top-14 border-t border-cod-200 absolute rotate-3" -->
    <!--   ></div> -->
    <!-- </div> -->
    <div class="h-12 bg-transparent relative">
      <div
        class="h-30 w-[120vw] bg-cod-50 -left-20 -top-15 border-t border-cod-200 absolute -rotate-3"
      ></div>
    </div>

    <!-- Resident Experts Section -->
    <section class="pt-12 pb-16 bg-cod-50">
      <UContainer>
        <h2 class="section-title">Meet Your Resident Experts</h2>
        <p class="text-xl mb-12 max-w-3xl">
          Get direct help from these experienced creators in our community.
        </p>

        <div
          class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-5 gap-2 md:gap-6"
        >
          <div
            v-for="expert in experts"
            :key="expert.name"
            class="bg-secondary-50 p-2 md:py-4 gap-4 rounded-xl overflow-hidden border border-secondary-300 md:text-center flex md:flex-col items-center"
          >
            <div class="flex items-center justify-center">
              <UAvatar
                v-if="expert.avatar"
                :src="expert.avatar"
                :alt="expert.name"
                size="xl"
                class="size-20 md:size-30 lg:size-36"
              />
            </div>
            <div>
              <h3 class="font-bold text-xl text-secondary-950">
                {{ expert.name }}
              </h3>
              <p class="text-md text-secondary-700">
                {{ expert.expertise }}
              </p>
            </div>
          </div>
        </div>
      </UContainer>
    </section>

    <!-- Library Section -->
    <section class="py-16 md:py-24">
      <UContainer>
        <h2 class="section-title space-x-1">
          <span> Access Our Library of </span>
          <span
            class="inline-block -rotate-1 bg-primary-200 font-bold px-2 py-1"
            ><span class="inline-block rotate-1"
              >{{ courses.length }}+ Courses</span
            ></span
          >
        </h2>
        <p class="text-xl mb-12 max-w-3xl">
          From building media businesses to mastering AI tools, our library has
          everything you need to start and grow your small bets.
        </p>

        <div class="grid grid-cols-1 lg:grid-cols-2 gap-2">
          <div
            v-for="(course, index) in courses"
            :key="index"
            class="bg-secondary-100/70 md:items-center ring-2 ring-secondary-400 text-black py-1 px-2 rounded-lg flex gap-1"
          >
            <div class="flex md:items-center pt-1 md:pt-0">
              <UIcon
                name="i-heroicons-chevron-right-16-solid"
                class="text-lg"
              />
            </div>
            <p class="font-medium text-secondary-900">{{ course }}</p>
          </div>
        </div>
      </UContainer>
    </section>

    <div class="h-12 bg-transparent relative">
      <div
        class="h-30 w-[120vw] bg-fall-50 -left-20 -top-5 border-t border-fall-200 absolute -rotate-3"
      ></div>
    </div>

    <!-- Pricing / Lifetime Membership Section -->
    <section class="py-16 md:py-24 bg-fall-50">
      <UContainer>
        <h2 class="section-title space-x-2">
          <span> One-Time Payment,</span>
          <span class="inline-block -rotate-1 bg-fall-200 font-bold py-1 px-2"
            ><span class="inline-block rotate-1">Lifetime Access</span></span
          >
        </h2>
        <p class="text-xl mb-12">
          No monthly fees, no upsells, just pure value that keeps growing.
        </p>

        <div class="max-w-2xl">
          <div>
            <div>
              <ul class="space-y-4">
                <li
                  v-for="(benefit, index) in benefits"
                  :key="index"
                  class="flex md:items-center gap-2"
                >
                  <div class="flex md:items-center pt-1 md:pt-0">
                    <UIcon class="text-2xl" name="i-heroicons-check-circle" />
                  </div>
                  <span class="text-lg">{{ benefit }}</span>
                </li>
              </ul>

              <div class="mt-8">
                <UButton
                  :to="joinNow"
                  size="xl"
                  variant="subtle"
                  color="primary"
                  class="w-full hover:ring-2 md:w-auto font-bold py-4 px-8 text-lg"
                  trailing-icon="i-heroicons-arrow-right-16-solid"
                >
                  Join Small Bets Now
                </UButton>
                <p class="mt-2 text-sm">
                  Join {{ members }} other members building small bets.
                </p>
              </div>
            </div>
          </div>
        </div>
      </UContainer>
    </section>

    <!-- Footer -->
    <footer class="py-4 bg-fall-50">
      <UContainer>
        <div class="flex flex-col md:flex-row items-center justify-between">
          <div class="flex items-center gap-2 mb-4 md:mb-0">
            <img class="rounded-lg h-8" src="/logo.jpg" />
            <span class="font-logo text-xl font-bold">Small Bets</span>
          </div>
          <div class="text-fall-950">
            © {{ new Date().getFullYear() }} Small Bets — Make money without
            risking it all.
          </div>
        </div>
      </UContainer>
    </footer>
  </div>
</template>

<script setup>
definePageMeta({
  colorMode: "light",
});

useSeoMeta({
  title: 'Small Bets: Build a Portfolio of Profitable Projects',
  ogTitle: 'Small Bets: Build a Portfolio of Profitable Projects',
  description: 'Join a community of solopreneurs and learn how to build profitable online projects. Access 45+ courses, expert advice, and a supportive network.',
  ogDescription: 'Join a community of solopreneurs and learn how to build profitable online projects. Access 45+ courses, expert advice, and a supportive network.',
})

const { signIn, joinNow } = useAppConfig().links;

// TODO: fetch this with an API?
const members = 6650;

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
  {
    name: "Arvid Kahl",
    quote:
      "This isn't just an **amazing community** for eager founders to learn in; it's also an expression of Daniel's expansive teaching mindset. Allowing people to teach themselves by re-living your past lectures is an active act of empowering those who already have an overflowing schedule.",
  },
  {
    name: "Florin Pop",
    quote:
      "There are **tons of webinars with amazing people**, and the community is full of amazing people.",
  },
  {
    name: "Tony Dinh",
    quote: "Small Bets is **the most active server** on my Discord!",
  },
  {
    name: "Espree Devora",
    quote:
      "Small Bets is the most high value engaged helpful business community on the internet. We pay a one time small fee for life time access to **quality connections and impactful education that transforms** our lives.",
  },
  {
    name: "Kenny Liu",
    quote:
      "I just finished the Small Bets lecture about Upwork with @SeanODowd15. **Countless gems for takeaway!** @dvassallo and his team continue to provide real value for the Small Bets community. So glad I signed up!",
  },
  {
    name: "Ergest Xheblati",
    quote:
      "Honestly the best community I've been a part of in the last 10 years",
  },
  {
    name: "Aprilynne Alter",
    quote:
      "I can easily say that the Small Bets community has been **one of the most engaged groups of people** I've had the pleasure of teaching! Great community there.",
  },
  {
    name: "Hassan Osman",
    quote:
      "This course by @dvassallo will show you: How to think about starting a business; How to reduce the risk of failure; How to use randomness to your advantage. **Truly one of the best courses I've taken**.",
  },
  {
    name: "Dan Rowden",
    quote:
      "The Discord is **full of amazing makers**. It's like a curated group of the best from Twitter, plus more interaction and value.",
  },
  {
    name: "Vic Vijayakumar",
    quote:
      "You get an active community Discord, lots of guest lectures (with recordings), tons of freebies (and/or discounts to various saas / ebooks / courses), and in my case I also **made some very good friends**.",
  },
  {
    name: "Monica Lim",
    quote:
      "You don't need another course but this by @dvassallo legit freed me from self-sabotage and procrastination. It's **value dense**, affordable and the community is still small and quite active.",
  },
  {
    name: "Manny de Souza",
    quote:
      "By far, the best content I consumed about entrepreneurship and lifestyle. It is amazing to be **among of so many like minded people**.",
  },
  {
    name: "Jeffrey Guenther",
    quote:
      "**Absolutely worth the price** of admission. It's like having access to a bunch of paid courses.",
  },
  {
    name: "Ankur Tyagi",
    quote:
      "If you're looking for an awesome community. If you're trying small bets and need **genuine feedback**. If you need to understand how randomness played a big role in your life. This is for you.",
  },
  {
    name: "Jeremy Smith",
    quote:
      "Daniel is solidifying many concepts I had some intuition/pattern matching for, but couldn't yet articulate. **Highly recommended**!",
  },
  {
    name: "George McEntegart",
    quote: "A community that **keeps giving value again and again**.",
  },
  {
    name: "Ankita Kulkarni",
    quote:
      "**Highly recommend it**, you start thinking in small bets vs taking on huge projects which cost you time and money!",
  },
  {
    name: "Rafael Rinaldi",
    quote: "This community truly is **the gift that keeps on giving**.",
  },
  {
    name: "Jordan Davis",
    quote:
      "Very few one-time purchases continue to add more and **more value over time** like this.",
  },
  {
    name: "Brock Briggs",
    quote: "The community is **absolutely invaluable**.",
  },
  {
    name: "Brandon Fearing",
    quote:
      "Joined @dvassallo small bets community yesterday and the guest lecture recordings are 100%. Found @searchbound's domain first development **super intriguing**. Maybe now I can put my 40+ unused domains to use!",
  },
  {
    name: "Hugo Hamel",
    quote:
      "It is so **refreshing and inspiring** to be part of the Small Bets community. It might be bad for the economy, but it's extremely healing in many ways to experience. Truly a beautiful community!",
  },
  {
    name: "Nick Hammond",
    quote:
      "Love being able to go back into the recordings on my own time. Appreciate **all of the info you've collected in one place**!",
  },
  {
    name: "Angad Singi",
    quote:
      "Being a part of smallbets.co, I love the community. The instant feedback, **quality conversations**, and exploring possibilities of digital business is superb.",
  },
  {
    name: "Corey Wilks",
    quote:
      "Shared the same wins in a few communities recently. **Nothing beats the supportiveness** of the Small Bets community.",
  },
  {
    name: "Shivam Dewan",
    quote:
      "smallbets.co is my **new idea generator**. If you need inspiration and a supportive community, this is the place to be. Been into so many discord groups but only this one I actually participate in.",
  },
  {
    name: "Travis Hayes",
    quote:
      "Highly recommend looking into Daniel's small bets community. As a new active twitter user, I often have a ton of questions. **The community is engaged** and has been helpful.",
  },
  {
    name: "Miche Priest",
    quote:
      "Taking this course and joining this Discord has been an incredible learning journey. Top notch, creative, generous, engaged people coming together to figure out how to design work around life. **Makings solopreneurship not so solo**.",
  },
  {
    name: "Enrique Benitez",
    quote:
      "Just finished this course by @dvassallo and it's by far **the best course I've ever taken**, Daniel explains and dissects the process of building a portfolio of small bets thoroughly, from product ideas, randomness and luck, making money and lifestyle design.",
  },
  {
    name: "Jason Akinaka",
    quote:
      "**Highly recommend** it for those who, like me, dread the 9-5 and have way too many interests to ever want to go back.",
  },
  {
    name: "Takamichi Okubo",
    quote:
      "Just finished @dvassallo's awesome cohort course. It's 9+ hours of **pure informativeness and inspiration**.",
  },
];

const formatTestimonial = (text) => {
  return text.replace(
    /\*\*(.*?)\*\*/g,
    '<span class="bg-secondary-200 px-1 font-bold">$1</span>',
  );
};

const showAllTestimonials = ref(false);
const toggleShowAllTestimonials = () => {
  showAllTestimonials.value = !showAllTestimonials.value;
};

const experts = [
  {
    name: "Daniel Vassallo",
    expertise: "Small Bets Strategy",
    avatar: "https://i.pravatar.cc/300?img=1",
  },
  {
    name: "Arvid Kahl",
    expertise: "Media Business",
    avatar: "https://i.pravatar.cc/300?img=12",
  },
  {
    name: "Jordan O'Connor",
    expertise: "Audience Building & SEO",
    avatar: "https://i.pravatar.cc/300?img=33",
  },
  {
    name: "Monica Lim",
    expertise: "Notion Expert",
    avatar: "https://i.pravatar.cc/300?img=25",
  },
  {
    name: "Sahil Lavingia",
    expertise: "Crowdfunding",
    avatar: "https://i.pravatar.cc/300?img=68",
  },
  {
    name: "Espree Devora",
    expertise: "Podcasting",
    avatar: "https://i.pravatar.cc/300?img=48",
  },
  {
    name: "Steph Smith",
    expertise: "Internet Marketing",
    avatar: "https://i.pravatar.cc/300?img=29",
  },
  {
    name: "Hassan Osman",
    expertise: "Course Creation",
    avatar: "https://i.pravatar.cc/300?img=53",
  },
  {
    name: "Sairam Sundaresan",
    expertise: "AI & GPT",
    avatar: "https://i.pravatar.cc/300?img=63",
  },
  {
    name: "Peter Askew",
    expertise: "Domain Development",
    avatar: "https://i.pravatar.cc/300?img=15",
  },
];

const benefits = [
  "Access to 45+ courses and workshops (worth $4,500+)",
  "Active Discord community with 6,500+ members",
  "Direct access to successful entrepreneurs",
  "Weekly live workshops and Q&A sessions",
  "All future courses and content at no extra cost",
  "Accountability groups to help you stay on track",
  "Early access to new tools and resources",
  "A supportive network to validate your ideas",
];
</script>
