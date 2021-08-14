<script lang="ts">
	// import Sidebar from "./Sidebar.svelte";

	let avatar: any, fileinput: any, imgText: string;
	let color: string = "#000000";
	let xPos: string = "0";
	let yPos: string = "0";
	let deg: string = "0";
	let imgB: string = "100";
	let imgC: string = "100";
	let imgSa: string = "100";
	let imgG: string = "0";
	let imgSe: string = "0";
	let imgBl: string = "0";
	let imgH: string = "0";

	const onFileSelected = (e) => {
		let image = e.target.files[0];
		let reader = new FileReader();
		reader.readAsDataURL(image);
		reader.onload = (e) => {
			avatar = e.target.result;
		};
	};

	const searchImg = () => {
		window.location.href = "https://www.google.com/imghp";
	};
</script>

<div class="editorGrid">
	<div class="editorCanvas">
		{#if avatar}
			<img
				class="avatar"
				style="--imgBrightness:{imgB}%; --imgContrast:{imgC}%;
						--imgSaturation:{imgSa}%; --imgGrayScale:{imgG}%;
						--imgSepia:{imgSe}; --imgBlur:{imgBl}px; --imgHueRotation:{imgH}deg;"
				src={avatar}
				alt="d"
			/>
			<div
				id="imgOverlay"
				style="--overLayColor: {color}; --overLayX: {xPos}%;--overLayY: {yPos}%; --overLayDeg: {deg}deg"
			>
				{#if imgText}
					<h1>{imgText}</h1>
				{/if}
			</div>
		{:else}
			<h2>No Image Found</h2>
		{/if}

		<button
			class="chooseImgBtn"
			on:click={() => {
				fileinput.click();
			}}>Choose / Change Image</button
		>
		<input
			style="display:none"
			type="file"
			accept=".jpg, .jpeg, .png"
			on:change={(e) => onFileSelected(e)}
			bind:this={fileinput}
		/>
	</div>
	<section>
		<div>
			<button on:click={searchImg}>Search Image</button>
			<button>Save Image</button>
		</div>
		{#if avatar}
			<details open>
				<summary>Tools</summary>
				<div class="detailsDiv">
					<div class="editToggleGrid">
						<label for="">Textbox</label>
						<input
							type="text"
							name=""
							id=""
							placeholder="Text Content"
							bind:value={imgText}
						/>
						<label for="">Text Color</label>
						<input type="color" bind:value={color} />
						<label for="">X axis</label>
						<input type="range" min="-100" max="100" bind:value={xPos} />
						<label for="">Y axis</label>
						<input type="range" min="-100" max="100" bind:value={yPos} />
						<label for="">Rotation</label>
						<input type="range" min="0" max="360" bind:value={deg} />
					</div>
				</div>
			</details>
			<details>
				<summary>Image Filters</summary>
				<div class="detailsDiv">
					<div class="editToggleGrid">
						<label for="">Brightness</label>
						<input type="range" min="-200" max="400" bind:value={imgB} />
						<label for="">Contrast</label>
						<input type="range" min="-200" max="400" bind:value={imgC} />
						<label for="">Saturation</label>
						<input type="range" min="-200" max="400" bind:value={imgSa} />
						<label for="">Grayscale</label>
						<input type="range" min="0" max="300" bind:value={imgG} />
						<label for="">Sepia</label>
						<input type="range" min="0" max="300" bind:value={imgSe} />
						<label for="">Blur</label>
						<input type="range" min="0" max="100" bind:value={imgBl} />
						<label for="">Hue Rotation</label>
						<input type="range" min="0" max="360" bind:value={imgH} />
					</div>
				</div>
			</details>
		{:else}
			<h4>Add Image To Display Editing Tools.</h4>
		{/if}
	</section>
</div>

<style>
	.editorGrid {
		padding-top: 1em;
		display: grid;
		grid-template-columns: 3fr 1fr;
		gap: 2em;
	}
	.editorCanvas {
		border: 2px solid black;
		box-shadow: 5px 5px black;
		padding: 1em;
		display: flex;
		align-items: center;
		justify-content: center;
		flex-direction: column;
		gap: 1em;
		min-height: 400px;
		height: min-content;
	}
	.avatar {
		border: 1px solid var(--editGrey);
		width: auto;
		min-width: 400px;
		max-width: 900px;
		overflow: hidden;
		height: auto;
		filter: brightness(var(--imgBrightness)) contrast(var(--imgContrast))
			saturate(var(--imgSaturation)) grayscale(var(--imgGrayScale))
			sepia(var(--imgSepia)) blur(var(--imgBlur))
			hue-rotate(var(--imgHueRotation));
	}

	#imgOverlay {
		z-index: 10;
		position: absolute;
		color: var(--overLayColor);
		transform: translate(var(--overLayX), var(--overLayY))
			rotate(var(--overLayDeg));
	}
	#imgOverlay h1 {
		font-size: 3em;
		text-shadow: 1px 0px 5px var(--editGrey);
	}

	details {
		margin-top: 1em;
		margin-bottom: 1em;
		cursor: pointer;
	}
	.detailsDiv {
		margin-top: 0.5em;
		border: 2px solid black;
		padding: 1em;
		display: grid;
		grid-template-columns: 1fr;
		gap: 0.2em;
	}
	.editToggleGrid {
		display: grid;
		grid-template-columns: 0.7fr 2fr;
		gap: 1em;
	}
</style>
