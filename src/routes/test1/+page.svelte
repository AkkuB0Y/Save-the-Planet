<div id="image-track" data-mouse-down-at= "0" data-prev-percentage="0">
    <img class="image" alt="image1" src="https://images.pexels.com/photos/889848/pexels-photo-889848.jpeg" draggable="false"/>
    <img class="image" alt="image2" src="https://images.pexels.com/photos/15153858/pexels-photo-15153858/free-photo-of-fishes-in-the-aquarium.jpeg?auto=compress&cs=tinysrgb&w=1200&lazy=load" draggable="false"/>
    <img class="image" alt="image3" src="https://images.pexels.com/photos/12616865/pexels-photo-12616865.jpeg?auto=compress&cs=tinysrgb&w=1200&lazy=load" draggable="false"/>
    <img class="image" alt="image4" src="https://images.pexels.com/photos/4987031/pexels-photo-4987031.jpeg?auto=compress&cs=tinysrgb&w=1200&lazy=load" draggable="false"/>
    <img class="image" alt="image5" src="https://images.pexels.com/photos/12616878/pexels-photo-12616878.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2" draggable="false"/>
    <img class="image" alt="image6" src="https://images.pexels.com/photos/6123092/pexels-photo-6123092.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=2" draggable="false"/>
    <img class="image" alt="image7" src="https://images.pexels.com/photos/10691795/pexels-photo-10691795.jpeg?auto=compress&cs=tinysrgb&w=1200&lazy=load" draggable="false"/>
    <img class="image" alt="image8" src="https://images.pexels.com/photos/13249403/pexels-photo-13249403.jpeg?auto=compress&cs=tinysrgb&w=1200&lazy=load" draggable="false"/>
</div>

<script>
    import { onMount } from 'svelte';
    onMount(async () => {
        const track = document.getElementById("image-track");

        const handleOnDown = e => track.dataset.mouseDownAt = e.clientX;

        const handleOnUp = () => {
        track.dataset.mouseDownAt = "0";  
        track.dataset.prevPercentage = track.dataset.percentage;
        }

        const handleOnMove = e => {
        if(track.dataset.mouseDownAt === "0") return;

        const mouseDelta = parseFloat(track.dataset.mouseDownAt) - e.clientX,
                maxDelta = window.innerWidth / 2;

        const percentage = (mouseDelta / maxDelta) * -100,
                nextPercentageUnconstrained = parseFloat(track.dataset.prevPercentage) + percentage,
                nextPercentage = Math.max(Math.min(nextPercentageUnconstrained, 0), -100);

        track.dataset.percentage = nextPercentage;

        track.animate({
            transform: `translate(${nextPercentage}%, -50%)`
        }, { duration: 1200, fill: "forwards" });

        for(const image of track.getElementsByClassName("image")) {
            image.animate({
            objectPosition: `${100 + nextPercentage}% center`
            }, { duration: 1200, fill: "forwards" });
        }
        }

        window.onmousedown = e => handleOnDown(e);
        window.ontouchstart = e => handleOnDown(e.touches[0]);
        window.onmouseup = e => handleOnUp(e);
        window.ontouchend = e => handleOnUp(e.touches[0]);
        window.onmousemove = e => handleOnMove(e);
        window.ontouchmove = e => handleOnMove(e.touches[0]);

    });
</script>