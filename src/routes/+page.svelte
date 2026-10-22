<script lang="ts">
	import type { HTMLButtonAttributes } from 'svelte/elements';
	import { Tabs } from '@skeletonlabs/skeleton-svelte';
	import { SparklesIcon, ArrowRightIcon, AppleIcon, MailIcon } from '@lucide/svelte/icons';

	let tabValue = $state('register');
	let routes = [
		{ label: 'Log in', value: 'login' },
		{ label: 'Criar Conta', value: 'register' }
	];
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
	<div class="mx-auto w-full flex-1 rounded-t-2xl bg-white p-6">
		<Tabs value={tabValue} onValueChange={(e) => (tabValue = e.value)}>
			<Tabs.List class=" flex items-center rounded-2xl border-none bg-gray-200 p-1.5">
				{#each routes as route}
					<Tabs.Trigger value={route.value} class="flex-1">
						{#snippet element(attributes)}
							<button
								{...attributes as HTMLButtonAttributes}
								class="w-full rounded-xl py-3 text-center text-sm font-medium text-gray-500
                                   transition-all hover:text-gray-700
                                   data-selected:bg-white data-selected:text-primary-500 data-selected:shadow-sm
                                   data-[state=active]:bg-white data-[state=active]:text-primary-500 data-[state=active]:shadow-sm"
							>
								{route.label}
							</button>
						{/snippet}
					</Tabs.Trigger>
				{/each}
			</Tabs.List>
			<div class="mb-3 text-black">
				<h1 class="text-lg font-extrabold">Monitore de formar inteligente</h1>
				<p class="text-xs font-extralight">Sua meta calórica está a uma foto de distância.</p>
			</div>
			<Tabs.Content value="login">
				<p class="text-black">Login</p>
			</Tabs.Content>
			<Tabs.Content value="register">
				<form class="mx-auto w-full max-w-md space-y-4">
					<fieldset class="space-y-2">
						<label class="label">
							<span class="label-text text-black">Email</span>
							<input
								class="w-full rounded-md border-none bg-gray-200 focus:ring-primary-500"
								type="email"
								placeholder="bite@exemplo.com"
							/>
						</label>
						<label class="label">
							<span class="label-text text-black">Senha</span>
							<input
								class="w-full rounded-md border-none bg-gray-200 focus:ring-primary-500"
								type="password"
								placeholder="••••••••"
							/>
						</label>
					</fieldset>
					<label class="flex items-center space-x-2">
						<input class="checkbox" type="checkbox" checked />
						<p class="text-xs font-light text-black">
							Eu concordo com os termos de privacidade da Bitwise.
						</p>
					</label>
					<button class="w-full rounded-xl bg-primary-500 p-4">
						<div class="flex items-center justify-center gap-2">
							<ArrowRightIcon className="size-elem-lg" />
							<p>Criar minha conta</p>
						</div>
					</button>
				</form>
				<div class="my-4 flex w-full items-center">
					<div class="flex-1 border-t border-gray-300"></div>
					<span class="px-4 text-sm text-gray-500">ou continue com</span>
					<div class="flex-1 border-t border-gray-300"></div>
				</div>
				<div class="flex w-full justify-center gap-2 text-black">
					<button class="flex-1 rounded-xl border-1 border-gray-300 p-4">
						<div class="flex items-center justify-center gap-3">
							<AppleIcon className="size-elem-lg" />
							<p>Apple</p>
						</div>
					</button>
					<button class="flex-1 rounded-xl border-1 border-gray-300 p-4">
						<div class="flex items-center justify-center gap-3">
							<MailIcon className="size-elem-lg" />
							<p>Google</p>
						</div>
					</button>
				</div>
				<div class="mt-3 text-center text-sm font-extralight text-black">
					<p>Já é um membro ? Clique <a href="blank_" class="text-primary-500">aqui.</a></p>
				</div>
			</Tabs.Content>
		</Tabs>
	</div>
</div>
