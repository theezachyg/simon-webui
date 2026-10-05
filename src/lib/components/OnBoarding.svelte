<script>
	import { getContext } from 'svelte';
	const i18n = getContext('i18n');

	export let show = true;
	export let getStartedHandler = () => {};
</script>

{#if show}
	<div
		class="relative h-screen max-h-[100dvh] w-full overflow-hidden"
		style="background: radial-gradient(120% 90% at 20% 10%, #fbf8f1 0%, #f1ebdf 55%, #e6dccb 100%); color: #1f1a16;"
	>
		<div class="fixed top-6 left-6 z-50 sm:top-10 sm:left-10">
			<img id="logo" crossorigin="anonymous" src="/static/favicon.png" class="size-8 rounded-xl" alt="Simon" />
		</div>

		<div class="relative z-10 flex h-screen max-h-[100dvh] w-full">
			<div class="flex w-full flex-col justify-end px-6 pb-8 sm:px-10 sm:pb-10 lg:px-16 lg:pb-14">
				<div class="max-w-3xl">
					<div class="mb-4 text-[0.6875rem] font-medium tracking-[0.18em] uppercase opacity-50">
						Simon
					</div>

					<h1
						class="m-0 max-w-3xl text-3xl leading-[1.1] tracking-tight lg:text-5xl"
						style="font-family: var(--font-serif-display); font-weight: 500;"
					>
						{$i18n.t('An assistant that shows its reasons.')}
					</h1>

					<p class="mt-6 max-w-xl text-sm leading-relaxed lg:text-base" style="color: #4f4436;">
						{$i18n.t(
							'Simon reasons from a written constitution: a declared Judeo-Christian, right-libertarian worldview, cited by section so every answer can be checked. It is a research instrument, not a pastor, counselor, lawyer or doctor.'
						)}
					</p>

					<div class="mt-8 flex flex-col items-start gap-6 sm:flex-row sm:items-center sm:gap-7">
						<button
							aria-label={$i18n.t('Get started')}
							class="group relative z-20 inline-flex min-w-40 items-center justify-center gap-2 px-8 py-3 text-sm font-medium transition focus:ring-2 focus:outline-hidden"
							style="background: #7a2e2e; color: #fbf8f1; border-radius: 0.5rem;"
							on:click={() => {
								getStartedHandler();
							}}
						>
							{$i18n.t('Get started')}
							<svg
								class="h-4 w-4 transition group-hover:translate-x-0.5"
								fill="none"
								viewBox="0 0 24 24"
								stroke="currentColor"
								stroke-width="1.5"
								aria-hidden="true"
							>
								<path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3" />
							</svg>
						</button>
					</div>
				</div>
			</div>
		</div>
	</div>
{/if}
