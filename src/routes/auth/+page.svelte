<script lang="ts">
	export let data;
	$: ({ supabase } = data);

	async function signInWithGithub(provider: 'github') {
		await supabase.auth.signInWithOAuth({
			provider,
			options: {
				redirectTo: `http://localhost:5173/auth/callback`
			}
		});
	}
</script>

<form method="POST" action="?/login">
	<label>
		Email
		<input name="email" type="email" />
	</label>
	<label>
		Password
		<input name="password" type="password" />
	</label>
	<button>Login</button>
	<button formaction="?/signup">Sign up</button>


</form>
	<button on:click={() => signInWithGithub('github')}>Sign in with GitHub</button>