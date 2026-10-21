<script lang="ts">
	import type { HTMLButtonAttributes } from 'svelte/elements';
	import { Tabs } from '@skeletonlabs/skeleton-svelte';
	import SparklesIcon from '@lucide/svelte/icons/sparkles';

	let tabValue = $state('login');
</script>

<div class="flex min-h-screen flex-col bg-primary-500">
	<div class="w-full p-6">
		<div class="mb-8 flex items-center gap-3">
			<div class="w-fit rounded-md bg-white p-3">
				<SparklesIcon class="text-primary-500" className="size-elem-lg" />
			</div>
			<div>
				<h1 class="text-2xl font-bold">Bitewise</h1>
			</div>
		</div>
		<div class="mb-2">
			<h1 class="text-2xl">Veja sua refeição, conheça seu combustível.</h1>
		</div>
		<p class="text-white/70">
			Tire uma foto e deixe a IA transformar cada prato em informações nutricionais simples e úteis.
		</p>
	</div>
	<div class="flex-1 rounded-t-2xl bg-white">
		<Tabs value={tabValue} onValueChange={(e) => (tabValue = e.value)}>
			<Tabs.List class="m-6 flex items-center rounded-2xl border-none bg-gray-200 p-1.5">
				<Tabs.Trigger value="login" class="flex-1">
					{#snippet element(attributes)}
						<button
							{...attributes as HTMLButtonAttributes}
							class="w-full rounded-xl py-3 text-center text-sm font-medium text-gray-500
                                   transition-all hover:text-gray-700
                                   data-selected:bg-white data-selected:text-primary-500 data-selected:shadow-sm
                                   data-[state=active]:bg-white data-[state=active]:text-primary-500 data-[state=active]:shadow-sm"
						>
							Log in
						</button>
					{/snippet}
				</Tabs.Trigger>
				<Tabs.Trigger value="register" class="flex-1">
					{#snippet element(attributes)}
						<button
							{...attributes as HTMLButtonAttributes}
							class="w-full rounded-xl py-3 text-center text-sm font-medium text-gray-500
                                   transition-all hover:text-gray-700
                                   data-selected:bg-white data-selected:text-primary-500 data-selected:shadow-sm
                                   data-[state=active]:bg-white data-[state=active]:text-primary-500 data-[state=active]:shadow-sm"
						>
							Criar conta
						</button>
					{/snippet}
				</Tabs.Trigger>
			</Tabs.List>
			<Tabs.Content value="login" class="p-6">
				<p class="text-black">Login</p>
			</Tabs.Content>
			<Tabs.Content value="register" class="p-6">
				<p class="text-black">Registro</p>
			</Tabs.Content>
		</Tabs>
	</div>
</div>
