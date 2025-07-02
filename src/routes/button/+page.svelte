<script lang="ts">
    let count1 = $state(16);
    const count1Clamped = $derived(Math.min(64, count1))
    let count2 = $state(16);
    const count2Clamped = $derived(Math.min(64, count2))
</script>


<div class="flex flex-row gap-8">
    <div class="bg-red-300 size-64 rounded-full grid justify-center items-center">
        <button onclick={() => count1 += 1} class="bg-amber-800 text-white rounded-full size-7" style="width: {count1Clamped}px; height: {count1Clamped}px;">
            {count1}
        </button>
    </div>
    
    <div class="bg-red-300 size-64 rounded-full grid justify-center items-center">
        <button onclick={() => count2 += 1} class="bg-amber-800 text-white rounded-full size-7" style="width: {count2Clamped}px; height: {count2Clamped}px;">
            {count2}
        </button>
    </div>
    
</div>