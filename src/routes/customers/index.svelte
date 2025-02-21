<script lang="ts" context="module">
  export const prerender = true;

  export async function load({ session }) {
    const customers = session.customers;
    return { props: { customers } };
  }
</script>

<script lang="ts">
  import CompanyBenefits from "$lib/components/customers/company-benefits.svelte";
  import Stories from "$lib/components/customers/stories.svelte";
  import Explore from "$lib/components/explore.svelte";
  import Hero from "$lib/components/hero.svelte";
  import Testimonials from "$lib/components/index/testimonials.svelte";
  import UsedBy from "$lib/components/index/used-by.svelte";
  import OpenGraph from "$lib/components/open-graph.svelte";
  import Quotes from "$lib/components/quotes.svelte";
  import SectionFeatures from "$lib/components/section-features.svelte";
  import Section from "$lib/components/section.svelte";
  import { developFeature, quotes, benefits } from "$lib/contents/customers";
  import { testimonials } from "$lib/contents/home/index";

  export let customers: any;
</script>

<style lang="postcss">
  :global(.feature-box) :global(.preview) {
    @apply col-start-2 !important;
  }
</style>

<OpenGraph
  data={{
    title: "Customer stories - Gitpod",
    description:
      "Learn how other companies leverage Gitpod to improve their developer experience, remote collaboration and security.",
    keywords:
      "case study, customer story, experience, review, benefit, companies",
  }}
/>

<Hero
  title="You are in good company"
  text="Learn how other customers leverage Gitpod to improve their developer experience, remote collaboration and security."
  image={{
    src: "/images/customers/hero.png",
    alt: "Gitpod Illustration image",
    isCut: false,
  }}
  btnPrimary={{
    href: "#stories",
    text: "View stories",
  }}
  btnSecondary={{
    href: "/contact/sales",
    text: "Contact sales",
  }}
/>

<CompanyBenefits {benefits} class="lg:pt-16" />

<Section>
  <Quotes {quotes} />
</Section>

<SectionFeatures
  title="Accelerate your workflow"
  text="Spin up fresh, automated developer environments for each task, in the cloud, in seconds."
  features={[{ ...developFeature, headingLevel: "h3" }]}
  type="box"
/>

<Stories
  title="Featured Customer Stories"
  text="Read how our customers improved their development workflows"
  id="stories"
  {customers}
  class="max-w-7xl lg:grid-cols-3 xl:px-4"
/>

<UsedBy
  isCard={false}
  class="py-small"
  title="Trusted by +500k developers"
  isCustomerStoriesLinkShown={false}
/>

<Testimonials {testimonials} style="margin-top: var(--small);" />

<Explore
  contents={{
    description:
      "Spin up fresh, automated dev environments for each task, in the cloud, in seconds - no contracts or banking details&nbsp;required.",
    secondaryLink: {
      href: "https://www.notion.so/gitpod/Gitpod-Onboarding-Guides-Stages-1-3-d97968210ad2408789e968597fe4633c",
      text: "View onboarding guides",
    },
  }}
/>
