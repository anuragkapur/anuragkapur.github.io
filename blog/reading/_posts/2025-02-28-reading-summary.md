---
layout: post
title:  "Feb 2025: What I read this month"
date:   2025-02-28 23:50:00 +0000
lastUpdatedDate: 2025-02-28 23:50:00 +0000
categories: reading highlight
tags: reading
teaser: February'2025 casual reading highlights including MetaAI Personalisation and Memory, AI for Deep Research, AI Action Summit, Small Modular Reactors SMRs, Trump, DOGE, Taking Your Kids Seriously
---  

# Artificial Intelligence

## MetaAI: Personalisation and Memory
Meta has been rolling out a feature where the AI chatbot remembers some info from your 1:1 conversations with it. For example, if you tell it you are vegan, and then at some point in the future ask it for restaurant recommendations, it would keep your dietary preferences in mind. Users will also have the ability to ask the AI to explicitly remember certain details about them or ask the AI to delete its memory about them at any time should they want to. Similar “memory” features already exist in ChatGPT and Gemini. 

Additionally, the AI will leverage some info from your profile information and activity across the Meta family of apps (FB, insta, WhatsApp) to personalise its responses. Personalisation could be a USP of the Meta AI compared to competitors, such as ChatGPT, because Meta knows “a lot” about specific interests and activities of users across its apps. 

### References
* [1] [about.fb.com, Jan 2025: Building Toward a Smarter, More Personalized Assistant](https://about.fb.com/news/2025/01/building-toward-a-smarter-more-personalized-assistant/)
* [2] [Engadget, Jan 2025: Meta AI will now use your Facebook and Instagram activity to inform its recommendations](https://www.engadget.com/social-media/meta-ai-will-now-use-your-facebook-and-instagram-activity-to-inform-its-recommendations-201218403.html)
* [3] [The Verge, Jan 2025: Meta AI will use its ‘memory’ to provide better recommendations](https://www.theverge.com/2025/1/27/24352992/meta-ai-memory-personalization)

## AI for Deep Research
OpenAI launched deep research, an AI agent capable of multi-step research on the Internet for complex tasks, in minutes compared to something a human would need hours to do. Uses o3 model. Though the reports produced have linked references, occasional hallucinations and inaccuracies have been reported by the early adopters. 

"Unlike traditional AI models that attempt one-shot answers, Deep Research first asks clarifying questions. It might ask four or more questions to make sure it understands exactly what you want. It then develops a structured research plan, conducts multiple searches, revises its plan based on new insights, and iterates in a loop until it compiles a comprehensive, well-formatted report" [3]

At a high level Deep Research combines (1) the power of reasoning LLMs (such as OpenAI's o3, DeepSeek's R1) with (2) agentic Retrieval-Augmented Generation (RAG) in ways that hasn't been done before in a mass-market product.

Perplexity, Google's Gemini, xAI's Grok 3, HuggingFace have also launched there versions of deep research agents. Unlike Gemini, Grok 3 and ChatGPT, Perplexity's research agent is built on top of DeepSeek's open source R1 model and offers a free tier usage to users. All other current deep research agents provided by OpenAI, Google and xAI are for paid subscribers only. HuggingFace's Open Deep Research is as the name suggests, open source.

Given the early version of all research agents, there are reports of inaccuracies and hallucination across most, highlighting the need to fact-check answers and research output from these AI models.

### References
* [1] [OpenAI.com, Feb 2025: Introducing deep research](https://openai.com/index/introducing-deep-research/)
* [2] [Mashable, Feb 2025: Perplexity's new Deep Research tool is powered by DeepSeek R1](https://mashable.com/article/perplexity-new-deep-research-tool-powered-by-deepseek-r1)
* [3] [VentureBeat, Feb 2025: ](https://venturebeat.com/ai/out-analyzing-analysts-openai-deep-research-pairs-reasoning-llms-with-agentic-rag-to-automate-work-and-replace-jobs/)

## AI Action Summit
The AI Action Summit, hosted by France and co-chaired by India, brought to light a shifting sentiment (at least from US and UK's point-of-view) away from security and regulation to a growth-focused AI agenda. US and UK did not sign the pledge that for "open", "inclusive" and "ethical" approach to the technology's development. The pledge was signed by other attendees including France, China, Japan, Canada, Australia and India.

### References
* [1] [BBC, Feb 2025: UK and US refuse to sign international AI declaration](https://www.bbc.co.uk/news/articles/c8edn0n58gwo)

## The AI Scene in China and DeepSeek
DeepSeek's launch has come with its share of controversy and debate. OpenAI claims it has found evidence the DeepSeek used outputs from OpenAI's models to train its LLM at a lower cost, process usually referred to as distillation. The broader implications of the launch of DeepSeek's R1 model a few weeks ago are still being understood. DeepSeek claimed that the final training step for R1 cost only $5.6mn. The figure, however, doesn’t include many other costs involved in developing its models, including computing infrastructure and previous training runs, making it hard to draw precise comparisons. 

Controversy and debate aside, experts acknowledge that the innovation in DeepSeek's work is in its use of Reinforcement Learning in developing the model. Large Language Models (LLMs) are created in two steps: (1) Pre-training where massive data sets requiring large compute power are used to help the model learn how to predict the next word in a sentence. (2) Post-training where the model is taught how to follow instructions such as solving math or coding problems. OpenAI pioneered and used Reinforcement Learning from Human Feedback (RLHF) to traing its LLM. However, this process is expensive and time consuming requiring humans labelling the model's responses to prompts to help the model learn which responses are the best. DeepSeek automated this final step using Reinforcement Learning (RL) where the model is rewarded to do the right thing and doesn't rely on an army of human labelers. 
	
A possible competitive advantage for DeepSeek, atleast amongst other Chinese AI companies is that DeepSeek hasn't raised any external financing, such as that from Chinese State-owned funds. This means it doesn't feel the pressure as some other companies to guarantee returns for the fear of losing the country's assets. While the precise claims around lower cost remain debated, it is clear DeepSeek has most the state-of-the-art forward as judged from praise from both Sam Altman and Mark Zuckerberg, with the latter crediting DeepSeek for making "advances that we will hope to implement in our systems".

DeepSeek has published its research and released its models in “open-weights” form, a more limited version of open-source software that allows anyone to download, use and modify the technology.

As the poster child of Chinese AI, DeepSeek is seeing rapid adoption in its home country. Several domestic cloud providers, car manufacturers, several local governments, hospitals, and state-owned-enterprises (SOEs) are among the early adopters of the technology. The shift in sentiment among previously conservative institutions is noticeable. The low cost of adoption of the open source R1 model seems to be playing its part in boosting adoption. Opinions may be split on whether this is genuine interest in adoption vs a result of superficial adoption so that institutions are seen in favour of the newest Chinese AI poster child. Interestingly DeepSeek doesn't seem to be directly benefiting from the surge in adoption because it allows its model to be downloaded and used for free. The cloud service providers hosting the model for use on the other hand are benefiting financially.

### References
* [1] [Financial Times, Jan 2025: DeepSeek’s ‘aha moment’ creates new way to build powerful AI with less money](https://on.ft.com/42zNGgS)
* [2] [Financial Times, Jan 2025: The global AI race: Is China catching up to the US?](https://on.ft.com/3WHuhGV)
* [3] [Financial Times, Feb 2025: DeepSeek spreads across China with Beijing’s backing](https://on.ft.com/3D8Bw4h)
 
## Musk's OpenAI Bid
Musk led a group of investors to make a $97.4 billion bid for the not-for-profit arm of OpenAI. Unclear what the real intention behind might be, some opinion pieces suggest this adds pressure on Altman and potentially messes with some of his plans to convert OpenAI into a for-profit company. 

Forbes reported: “He’s attempted to forcefully raise the nonprofit price – which would make it harder for OpenAI to justify paying anything less.”

### References
* [1] [Wall Street Journal, Feb 2025: Elon Musk-Led Group Makes $97.4 Billion Bid for Control of OpenAI](https://www.wsj.com/tech/elon-musk-openai-bid-4af12827)
* [2] [Forbes, Feb 2025: How Elon Musk Tried To Jack Up The Price Of OpenAI's Nonprofit Overnight](https://www.forbes.com/sites/richardnieva/2025/02/11/elon-musk-sam-altman-openai-bid-price/)

## Alexa+ Launch
Amazon launched Alexa+ service, embedding generative AI into the Alexa product line, with an aim to bring personalised and conversational Alexa experience. Alexa+ was originally touted to be launched over a year ago, following ChatGPTs launch. Not clear what were the primary factors behind the delay. Alexa+ comes with agentic capabilities enabling it to navigate the internet to make restaurant reservations, order groceries, book home appliance repairs etc. Its also personalised, remebering the user's past behaviours and preferences, somewhat similar to the personalisation capabilities Meta AI is bringing to its users. The service is included in the Prime subscription price, i.e. free for Prime members.

### References
* [1] [Financial Times, Feb 2025: Amazon debuts updated Alexa chatbot in push to catch up with rivals](https://on.ft.com/41yPh5Q)
* [2] [about.amazon.com, Feb 2025: The all-new Alexa+ and more: All the news from Amazon’s 2025 devices event](https://www.aboutamazon.com/news/devices/amazon-2025-devices-alexa-event-live-updates)

# Nuclear Energy

## Small Modular Reactors (SMRs)
Fission based nuclear reactors with a typical (not a strict limit) power capacity of up to 300MW, which is roughly a third of that of a conventional nuclear reactor. A key advantage of SMRs is their modular design where prefabricated units can be assembled together to have a functioning reactor, thus limiting the risks and delays associated with onsite construction.

SMR  design and development field is still in its early days, with known operational SMRs limited to a handful in Russia and China. UK government plans to make a decision on 2 SMRs by 2029, and have the first SMRs operational in the UK sometime in the 2030s.

Some backers of SMRs argue they are safer than large plants because they are simpler. They are still splitting the atom so they will still generate nuclear waste.

It is believed that SMRs can play a big role in powering energy hunry data centers supporting the growing use of AI.

### References
* [1] [International Atomic Energy Agency, Sep 2023: What are Small Modular Reactors (SMRs)?](https://www.iaea.org/newscenter/news/what-are-small-modular-reactors-smrs)
* [2] [Financial Times, Jan 2025: Small nuclear reactors are coming, but big is still better](https://on.ft.com/4g46x6O)
* [3] [The Times, Feb 2025: How do small nuclear reactors work and why would they help Britain?](https://www.thetimes.com/uk/environment/article/how-mini-nuclear-reactor-work-pm9tq6l2v)

## Fusion
Helion, a start-up aiming to produce electicity using Nuclear Fusion by 2028, has raised $425mn in funding from investors including Sam Altman and Peter Thiel. 

The attraction to fusion comes from the fact that it's carbon-free and doesn't create long lived radio active waste. The radioactive waste generated from fusion has a much shorter half-life compare to that generated by fission. The challenge though is that to-date scientists have not been able to sustain fusion reactions for long enough time periods. China based researchers set a new world record of sustaining a fusion reaction for 1,066 seconds in Jan 2025.

### References
* [1] [Financial Times, Jan 2025: US nuclear fusion start-up backed by Sam Altman and Peter Thiel secures $425mn](https://on.ft.com/40xNxbi)

# Trump Administration

## DOGE
Trump and Musk defended DOGE actions by saying they are trying to tackle the Trillion dollar deficit that US faces, by removing fraud and abuse from the government. Musk was vocal about all of DOGE actions being very transparent (posted on the DOGE handle on X and the DOGE website), saying that is how you gain trust from the people. Nevertheless, the work DOGE is doing has attracted enough controversy and legal action. Some of their actions have been blocked by Judges, but Trump believes this simply delays the process. What they are doing is for the benefit of the country and that they would appeal any blockages from the justice system.

### References
* [1] [Youtube, Feb 2025](https://www.youtube.com/watch?v=UIsP1KkSZmM)
* [2] [Financial Times, Feb 2025: Elon Musk barred from accessing US Treasury payments data](https://www.ft.com/content/097b286f-376e-40eb-8804-69a6d217803d)

## Trump and Trade Policies
Announced 25% tariff on Steel and Aluminium imports and plans to introduce reciprocal tariffs across a wide range of countries that charge levis on US exports. This is after announcing 25% tariffs on all imports from neighbouring Canada and Mexico at the beginning of Feb, but then pausing them for 30 days, 2 days after the announcement. Also introduced a 10% levy on Chinese imports. These make up initial set of tariffs and the administration intends to introduce tariffs more broadly including on European imports. 

Trump’s rationale is that tariffs bring in lots of money for the government and give domestic products a boost. Additionally, he aims to close the trade deficit in the country. However, some economists believe this will out burden on the common people because the tariffs are paid by the US entity importing the goods and these costs are usually passed on to the consumers. Now in the long run, do these tariffs boost the US economy or put more burden on it, is to be seen. 

### References
* [1] [The Guardian, Jan 2025: Trump to impose tariffs on imports from Canada, Mexico and China](https://www.theguardian.com/us-news/2025/jan/31/trump-tariffs-canada-mexico-china)
* [2] [Financial Times, Jan 2025: Donald Trump threatens to ignite era of trade wars with new tariffs](https://on.ft.com/3PV68sS)
* [3] [Financial Times, Feb 2025: Trump to impose 25 per cent tariffs on steel and aluminium imports](https://on.ft.com/40UpL9o)

## Ukraine - Russia War
Trump spoke with Putin about the war in Ukraine and how it might be brought to an end. Options on the table include Ukraine ceding 20% of its pre-war territory based on where the current battle-lines are. Ukraine’s membership to NATO seems to be off the table because that’s not something Putin is likely to accept as part of negotiations. While US is playing a role in the negotiations, they seem to not be willing to provide further aid to rebuild Ukraine and contribute to post-war security. Instead US expects Europe to take charge of that, which is something that worries EU.  

Trump's direction of travel in diplomacy does not look good for Ukraine, given the transactional nature of US foreign policy. US indicated they would want control over some of Ukraine’s natural resources in exchange for its contributions to ending the war. Atleast initially, Zelensky has declined this demand/expectation. 

### References
* [1] [Washington Post, Feb 2025: Trump Says He and Putin Agreed to Begin Talks on Ending Ukraine War](https://www.washingtonpost.com/national/2025/02/12/russia-us-marc-fogel-prisoner-swap/a5c50720-e92e-11ef-969b-cfbefacb1eb3_story.html)
* [2] [Financial Times, Feb 2025: Europe reels after Donald Trump announces US-Russia talks on Ukraine](https://on.ft.com/4hMHG96)
* [3] [Sky News, Feb 2025: Donald Trump's direction of travel in diplomacy does not look good for Ukraine](https://news.sky.com/story/donald-trumps-direction-of-travel-in-diplomacy-does-not-look-good-for-ukraine-13312187)

# Data Centres on the Moon
[IntuitiveMachines](https://www.intuitivemachines.com/) is launching a mini data centre to the moon via SpaceX's Falcon 9 rocket. The lunar surface which has almost no atmosphere doesn't come with the worry of climate related disruptions such as hurricanes and earthquakes. Certain parts of the moon are permanently shadowed from the sun and are thus extremly cold meaning no energy or water is needed to cool data centers. Likewise solar energy from the always thats almost always available in certain parts of the moon can be harnessed to power these data centres. Theoretically, data centers can be hidden away from the sun and power can be transmitted to them, resulting in perfectly renewable operation at low temperature. The challenges include the fact that the moon is far away, leading to one-way latency to the earth of 1.4 seconds, which rules out data that needs to be accessed in real time.

## References
* [1] [IEEE Spectrum, Feb 2025: We're Testing Out Data Centers on the Moon](https://spectrum.ieee.org/data-center-on-the-moon)

# How to Raise a Sovereign Child, A Freedom-Maximizing Approach to Parenting
"How to Raise a Sovereign Child", based on the philosphy of "Taking your Children Seriously", advocates for a parenting approach that prioritizes children's autonomy and freedom. It emphasizes treating children with the same respect afforded to adults. Encourages parents to minimize control and maximize children's ability to make their own choices.

The philosophy is described in the book [The Sovereign Child: How a Forgotten Philosophy Can Liberate Kids and Their Parents](https://www.amazon.co.uk/Sovereign-Child-Forgotten-Philosophy-Liberate-ebook/dp/B0DR36P28C) by Aaron Stupple. Aaron is a parent of 5 himself. The podcast is joined by Naval Ravikant, parent and among other claims to fame, the co-founder of Angel List. 

* Everytime you force your child to do something, you set yourself up as an adversary for them; you want your kids to not eat too much chocolate because it's not good for them not because Dad stops them from eating chocolate; easier said than done though?
* Example: Instead of forcing your child to brush their teeth, maybe understand why they are pushing back on your ask for them to brush? Maybe the "problem" is that they don't like the taste or feel of the toothbrush. A possible approach could be going to the supermarket with your kid and letting them chose their favourite toothpast from the aisle or their favourite peppa pig toothbrush. Another possibility is showing them or talking to them about how germs would eat away their teeth if they don't brush their teeth.
* Naval's kids eat what they want, sleep and wake up when they want, have as much screen time as they want, are home schooled; Naval says, despite all their freedom they are farily well developed, to the same levels as their peers with more mainstream parenting; Only constraints or rules Naval imposes are around Math and Reading - after the kids have done their daily Math and Reading then they are free to do what they want
* Building knowledge beats coercion, but won't it be exhausting to reason everything with a 3 year old? It is hard work, but more like a one-time upfront investment. Example: Once you've explained to your kid why putting on mittens is important before venturing out in the cold, you won't be needing to spending time with the push and tantrums to put on mittens everytime they go out - once the problem is solved, to the kids own understanding, it's solved for the rest of their life
* Naval's foundational non-negotiables: literacy, numeracy, computer literacy; if your kid doesn't understand basic gemotry and then one day you start talking about sunlight and refraction, they'd lose interest quickly because they lack the foundational skill and sometimes it is too late to build a foundational skill; if someone doesn't undestand basic math at the age of 18, then it's probably too late
* How do you get your kids to learn the non-negotiables? Requires way more active parenting. For example, with the right investment you can make math fun - via apps, games etc
* A litmus test: if you wouldn't speak to your spouse a certain way, don't speak that way to your child

## References
* [1] [Tim Ferriss' Blog, Jan 2025](https://tim.blog/2025/01/18/naval-ravikant-sovereign-child/)
* [2] [The Book on Amazon](https://www.amazon.co.uk/Sovereign-Child-Forgotten-Philosophy-Liberate-ebook/dp/B0DR36P28C)
  
# What is this?
Just trying to carve out time to read/watch/learn more when I can. Posting about it somewhat publicly is meant to nudge me when the motivation starts to dwindle.

Inspired by [Chamath Palihapitiya's What I read this week](https://chamath.substack.com/) series.
