<script>
    import { onMount } from 'svelte';

    let time = new Date()
    const dateFormatter = new Intl.DateTimeFormat('default', { 
        year: 'numeric', month: 'short', day: 'numeric',
        hour: 'numeric', minute: 'numeric'
    })

    $: formatted = dateFormatter.format(time).replace(',', '')

    onMount(() => {
        const interval = setInterval(() => {
            time = new Date();
        }, 1000)

        return () => {
            clearInterval(interval)
        }
    })
</script>

{formatted}

