<div class="h-screen grid grid-cols-12 grid-rows-6">
    <div class="bg-blue-400 col-start-1 col-end-3 row-start-1 row-end-4"></div>
    <div class="bg-rose-100 col-start-3 col-end-7 row-start-1 row-end-6"></div>
    <div class="bg-blue-400 col-start-7 col-end-13 row-start-1 row-end-3"></div>
    <div class="bg-teal-400 col-start-1 col-end-3 row-start-4 row-end-6"></div>
    <div class="bg-yellow-100 col-start-7 col-end-11 row-start-3 row-end-7 flex items-center justify-center">
        <div class="sticker">
            <div class="circle bg-yellow-100">
                <div class="left-triangle"></div>
                <div class="right-triangle"></div>
            </div>
        </div>
    </div>
    <div class="bg-emerald-400 col-start-11 col-end-13 row-start-3 row-end-7"></div>
    <div class="bg-fuchsia-400 col-start-1 col-end-7 row-start-6 row-end-7"></div>
</div>

<style lang="postcss">
    .sticker{
        width: 300px;
        height: 300px;
        background-color: #293462;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .circle{
        width: 200px;
        height: 200px;
        border-radius: 50%;
        overflow: hidden;
        position: relative;
    }

    .left-triangle{
        width: 0;
        height: 0;
        border-bottom: 100px solid #fe5f55;
        border-right: 100px solid transparent;
        border-left: 100px solid transparent;
        position: absolute;
        top: 129px;
        left: -71px;
    }
    .right-triangle{
        width: 0;
        height: 0;
        border-bottom: 200px solid #fe5f55;
        border-right: 200px solid transparent;
        border-left: 200px solid transparent;
        position: absolute;
        top: 59px;
        left: -59px;
    }
</style>
