<script lang="ts">
  import type { Testimonial } from "$lib/types/testimonial.type";
  export let testimonial: Testimonial;

  const { name, avatar, role, org, text, twitterHandle, tweetId } = testimonial;
</script>

<style lang="scss">
  .testimonial {
    scroll-snap-align: start;

    @media (max-width: 768px) {
      width: 320px;
    }
  }

  .testimonial :global(a) {
    color: var(--blue);
    font-weight: 600;
  }

  .testimonial :global(p) + :global(p) {
    margin-top: var(--macro);
  }

  .role :global(span) {
    font-weight: bold;
  }
</style>

<a
  href={`https://twitter.com/${twitterHandle}/status/${tweetId}`}
  target="_blank"
  data-analytics={`{"variant":"social_media","context":"socialproof","label":"` +
    name +
    `"}`}
  class="my-2 text-small"
  rel="noreferrer"
>
  <div
    class="testimonial stroked stroked-light w-96 p-xx-small overflow-hidden rounded-2xl bg-white dark:bg-card hover:shadow-xl transition-shadow duration-300 ease-in-out text-body"
  >
    <div>{@html text}</div>
    <div class="mt-4 flex">
      <img
        src={`/images/avatars/${avatar}`}
        alt={name}
        class="w-12 h-12 rounded-full"
        width="48"
        height="48"
      />
      <div class="ml-3">
        <p class="mb-0 font-semibold text-small leading-6 text-important">
          {name}
        </p>
        <p class="role">{role} {@html org}</p>
      </div>
    </div>
  </div>
</a>
