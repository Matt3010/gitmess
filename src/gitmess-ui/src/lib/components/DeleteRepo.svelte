<script lang="ts">
    import { initializeStores, Drawer } from "@skeletonlabs/skeleton";
    import { getDrawerStore } from "@skeletonlabs/skeleton";

    initializeStores()

    const drawerStore = getDrawerStore();

    function myClick() {
        drawerStore.open()
    }

    export let repoName: string = ""
</script>


<button on:click={myClick}>
    <img src="/trash.png" alt="trash_button" class="w-10" />

    <Drawer width="h-full px-12" position="bottom" >
        <div class="w-full h-full flex justify-center items-center text-black">
            <div class="flex flex-col items-center">
                Are you sure do you want delete "{repoName}"?
                <div class="flex mt-3">
                    <button type="button" class="btn variant-filled-error mr-3">Yes</button>
                    <button type="button" class="btn variant-filled">No</button>
                </div>
            </div>
        </div>
    </Drawer>
</button>