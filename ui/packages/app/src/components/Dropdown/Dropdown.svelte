<script lang="ts">
	import { Dropdown } from "@gradio/form";
	import { Block } from "@gradio/atoms";
	import StatusTracker from "../StatusTracker/StatusTracker.svelte";
	import type { LoadingStatus } from "../StatusTracker/types";
	import type { Styles } from "@gradio/utils";

	export let label: string = "Dropdown";
	export let info: string | undefined = undefined;
	export let elem_id: string = "";
	export let visible: boolean = true;
	export let value: string | Array<string> = [];
	export let multiselect: boolean = false;
	export let choices: Array<string>;
	export let show_label: boolean;
	export let style: Styles = {};
	export let loading_status: LoadingStatus;

	export let mode: "static" | "dynamic";
</script>

<Block
	{visible}
	{elem_id}
	disable={typeof style.container === "boolean" && !style.container}
>
	<StatusTracker {...loading_status} />

	<Dropdown
		bind:value
		{choices}
		{multiselect}
		{label}
		{info}
		{show_label}
		on:change
		disabled={mode === "static"}
	/>
</Block>
