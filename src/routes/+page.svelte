<script>
    import { onMount } from "svelte";
    let animalData = {
        "0": {
            name: "Amur Leopard",
            wikiURL: "https://en.wikipedia.org/wiki/Amur_leopard",
            imgURL: "https://images.unsplash.com/photo-1456926631375-92c8ce872def?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1170&q=80",
        },
        "1": {
            name: "Black Rhino",
            wikiURL: "https://en.wikipedia.org/wiki/Black_rhinoceros",
            imgURL: "https://images.unsplash.com/photo-1535338454770-8be927b5a00b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1000&q=80",
        },
        "2": {
            name: "Bornean Orangutan",
            wikiURL: "https://en.wikipedia.org/wiki/Bornean_orangutan",
            imgURL: "https://encrypted-tbn3.gstatic.com/licensed-image?q=tbn:ANd9GcSsN5b5P1Drt5sMjXat-0m9gf_TWPpC1kSlJ1Kt0SwxiUFqNcWaTsFxwSXepmOuEbOsK6ypqpjB4V5xTk4",
        },
        "3": {
            name: "Cross River Gorilla",
            wikiURL: "https://en.wikipedia.org/wiki/Cross_River_gorilla",
            imgURL: "https://u4d2z7k9.rocketcdn.me/wp-content/uploads/2023/04/cross-river-gorilla.jpg",
        },
        "4": {
            name: "Hawksbill Turtle",
            wikiURL: "https://en.wikipedia.org/wiki/Hawksbill_sea_turtle",
            imgURL: "https://images.unsplash.com/photo-1437622368342-7a3d73a34c8f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTd8fGhhd2tzYmlsbCUyMHR1cnRsZXxlbnwwfHwwfHx8MA%3D%3D&auto=format&fit=crop&w=1600&q=60",
        },
        "5": {
            name: "Sumatran Elephant",
            wikiURL: "https://en.wikipedia.org/wiki/Sumatran_elephant",
            imgURL: "https://encrypted-tbn0.gstatic.com/licensed-image?q=tbn:ANd9GcQU4Q927jJG3KiJpZYCTiaD1yaADfxYrU2BMCd4pn1lMTbG7uGqwaHINsdI6b9qVZeM0EpfYgjleihw7GU",
        },
        "6": {
            name: "Huso Huso",
            wikiURL: "https://en.wikipedia.org/wiki/Beluga_(sturgeon)",
            imgURL: "https://wwfint.awsassets.panda.org/img/original/huso_huso_schoenbrunn_phyllis.jpg",
        },
        "7": {
            name: "Sumatran Tiger",
            wikiURL: "https://en.wikipedia.org/wiki/Sumatran_tiger",
            imgURL: "https://encrypted-tbn2.gstatic.com/licensed-image?q=tbn:ANd9GcS_fdQpM2TuDpMcOcu53qjie_UNGIdw6eg1zjktHbK7XGi4efuTbLVBPr-CRpXgN29txtM52pg_xH-eedU",
        },
        "8": {
            name: "Vaquita",
            wikiURL: "https://en.wikipedia.org/wiki/Vaquita",
            imgURL: "https://2.bp.blogspot.com/-nX3LUbSMlos/V8Z-eWTx-YI/AAAAAAAAA1w/3GD-JUXMNeUbKgskif69KKe6smbc8KcXQCLcB/w1200-h630-p-k-no-nu/Cq2CasSWgAEPIv-.jpg",
        },
        "9": {
            name: "Javan Rhino",
            wikiURL: "https://en.wikipedia.org/wiki/Javan_rhinoceros",
            imgURL: "https://media.savetherhino.org/prod/uploads/2018/04/Javan-Rhino-Alain-Compost-1-1-768x499.jpg",
        },
        "10": {
            name: "Mountain Gorilla",
            wikiURL: "https://en.wikipedia.org/wiki/Mountain_gorilla",
            imgURL: "https://i.pinimg.com/originals/6a/b2/ca/6ab2ca810385a51bceaf13578093a450.jpg",
        },
        "11": {
            name: "Saola",
            wikiURL: "https://en.wikipedia.org/wiki/Saola",
            imgURL: "https://www.thetimes.co.uk/imageserver/image/%2Fmethode%2Ftimes%2Fprodmigration%2Fweb%2Fbin%2Fe8825800-a520-3f6e-ad7d-75a752da3419.jpg?crop=1500%2C1000%2C0%2C0",
        },
        "12": {
            name: "South China Tiger",
            wikiURL: "https://en.wikipedia.org/wiki/South_China_tiger",
            imgURL: "https://upload.wikimedia.org/wikipedia/commons/8/81/2012_Suedchinesischer_Tiger.JPG",
        },
        "13": {
            name: "Kakapo",
            wikiURL: "https://en.wikipedia.org/wiki/Kākāpō",
            imgURL: "https://cdn.sci.news/images/enlarge9/image_10051e-Kakapo.jpg",
        },
        "14": {
            name: "Yangtze Finless Porpoise",
            wikiURL: "https://en.wikipedia.org/wiki/Yangtze_finless_porpoise",
            imgURL: "https://upload.wikimedia.org/wikipedia/commons/d/dc/Yangtze_finless_porpoise%2C_10_November_2006.jpg",
        },
        "15": {
            name: "Ethiopian Wolf",
            wikiURL: "https://en.wikipedia.org/wiki/Ethiopian_wolf",
            imgURL: "https://adventure.com/wp-content/uploads/2018/10/Hero-Ethiopian-wolf-Bale-Mountains-Photo-credit-Shutterstock-1920x1080.jpg",
        },
        "16": {
            name: "Hawaiian Monk Seal",
            wikiURL: "https://en.wikipedia.org/wiki/Hawaiian_monk_seal",
            imgURL: "https://www.marinemammalcenter.org/storage/app/uploads/public/1ce/978/dfb/thumb__1600_0_0_0_crop.jpg",
        },
        "17": {
            name: "Indus River Dolphin",
            wikiURL: "https://en.wikipedia.org/wiki/Indus_river_dolphin",
            imgURL: "https://encrypted-tbn1.gstatic.com/licensed-image?q=tbn:ANd9GcQEr-sV7VdtaS_FALmBiCqsCJkS-3eSI_0CZRJQITgfpjIdD58mNEaee9nmsdWvIK8dqeUTKiV2oVdNMwY",
        },
        "18": {
            name: "Irrawaddy Dolphin",
            wikiURL: "https://en.wikipedia.org/wiki/Irrawaddy_dolphin",
            imgURL: "https://encrypted-tbn0.gstatic.com/licensed-image?q=tbn:ANd9GcRDdP_FOWr8Jjh9_oe0CMDyUIN367F9jdV4XGteR7c6vZoD3VP_ZZGXGANZVbBr-y2LriAiEELXwqC7r2I",
        },
        "19": {
            name: "Philippine Eagle",
            wikiURL: "https://en.wikipedia.org/wiki/Philippine_eagle",
            imgURL: "https://imgs.mongabay.com/wp-content/uploads/sites/20/2023/03/14125116/PEF_Klaus-Nigge-photos_the-Philippines-top-carnivore-is-a-Bird-of-Prey-the-Philippine-Eagle01.jpg",
        },
    };

    onMount(async () => {
        const track = document.getElementById("image-track");

        const handleOnDown = (e) => (track.dataset.mouseDownAt = e.clientX);

        const handleOnUp = () => {
            track.dataset.mouseDownAt = "0";
            track.dataset.prevPercentage = track.dataset.percentage;
        };

        const handleOnMove = (e) => {
            if (track.dataset.mouseDownAt === "0") return;

            const mouseDelta =
                    parseFloat(track.dataset.mouseDownAt) - e.clientX,
                maxDelta = window.innerWidth / 2;

            const percentage = (mouseDelta / maxDelta) * -100,
                nextPercentageUnconstrained =
                    parseFloat(track.dataset.prevPercentage) + percentage,
                nextPercentage = Math.max(
                    Math.min(nextPercentageUnconstrained, 0),
                    -100
                );

            track.dataset.percentage = nextPercentage;

            track.animate(
                {
                    transform: `translate(${nextPercentage}%, -50%)`,
                },
                { duration: 1200, fill: "forwards" }
            );

            for (const image of track.getElementsByClassName("image")) {
                image.animate(
                    {
                        objectPosition: `${100 + nextPercentage}% center`,
                    },
                    { duration: 1200, fill: "forwards" }
                );
            }
        };

        window.onmousedown = (e) => handleOnDown(e);
        window.ontouchstart = (e) => handleOnDown(e.touches[0]);
        window.onmouseup = (e) => handleOnUp(e);
        window.ontouchend = (e) => handleOnUp(e.touches[0]);
        window.onmousemove = (e) => handleOnMove(e);
        window.ontouchmove = (e) => handleOnMove(e.touches[0]);

        var icon = document.getElementById("icon");

        icon.onclick = function() {
            document.body.classList.toggle("dark-bg");
            if(document.body.classList.contains("dark-bg")) {
                icon.src = "https://upload.wikimedia.org/wikipedia/commons/thumb/d/db/Sun_white_icon.svg/1200px-Sun_white_icon.svg.png";
            }
            else {
                icon.src = "https://www.pngmart.com/files/13/Crescent-Moon-Transparent-Images-PNG.png";
            }
        }

    });
</script>

<!-- HTML Stuff -->


<nav>
    <div style="text-align:right; margin: 1rem 0.5rem">
        <a style = "margin: 0.2%" class = "link-btn" target = "_blank" href ="https://support.worldwildlife.org/site/SPageServer?pagename=main_monthly&s_src=AWE2306OQ18299A01179RX&s_subsrc=topnav&_gl=1*1a5b50u*_ga*MTU4NjQ2MTgzMy4xNjg2Nzc1MjU1*_ga_FK6M9RK84Z*MTY4Njc4Mjk2Ny4zLjEuMTY4Njc4NDk1NC42MC4wLjA.&_ga=2.26611893.985189242.1686775255-1586461833.1686775255">
        Donate</a>
        <a style = "margin: 0.2%" class = "link-btn" target = "_blank" href ="https://youtu.be/PkADl0HubMY"> Source </a>
        <img alt="darkmode" src="https://www.pngmart.com/files/13/Crescent-Moon-Transparent-Images-PNG.png" class = "dmbutton" id = "icon" style = "vertical-align: middle">
    </div>
    
</nav>

<h1 style="font-size: 3rem; margin: 0.75rem 2rem" class = "txtcolor">
    <center>Let's Save Our <span class = "txtcolor2">Planet.</span></center>
</h1>

<img alt="drag anywhere to move" src="https://icons.veryicon.com/png/o/miscellaneous/small-face-icon/left-arrow-28.png" class = "dragthing" draggable="false">
<p class = "txtdragthing"> Click and Drag!</p>

<div id="image-track" data-mouse-down-at="0" data-prev-percentage="0" class = "anti-highlight" style = "margin-top: 2rem; padding-left: 10px">
    {#each Object.entries(animalData) as [id, data]}
        <div class="image-container">
            <img
                class="image"
                alt=""
                src={data.imgURL}
                draggable="false"
            />
            <div class="learn-more-overlay">
                <a class = "learn-more-linkbtn" target = "_blank" href="{data.wikiURL}">Learn More.</a>
            </div>
            <p class="animal-name">{data.name}.</p>
        </div>
    {/each}
</div>

<p style="font-size: 1rem; top: 30%" class="txtcolor"><center>As our society progresses technologically, we often fail to consider the most vulnerable inhabitants of our planet - Animals.
    As such, I have created this little photo gallery to showcase some of the most beautiful yet threatened species on this planet we call home. Drag anywhere to see the gallery!
</center></p>




