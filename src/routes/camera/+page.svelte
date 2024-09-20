<script>
// @ts-nocheck

  import { onMount, onDestroy } from 'svelte';
  /**
     * @type {HTMLVideoElement}
     */
  let videoRef;
  /**
     * @type {HTMLInputElement}
     */
  let fileInput;
  /**
     * @type {MediaProvider | null}
     */
  let stream;
  /**
     * @type {string | null}
     */
  let uploadedFileUrl = null;

  // Start live video capture from the camera
  async function startVideo() {
    stopVideo(); // Ensure any previous video stream is stopped
    stream = await navigator.mediaDevices.getUserMedia({ video: true });
    videoRef.srcObject = stream;
    videoRef.play();
    videoRef.src = ''; // Clear any uploaded video
    uploadedFileUrl = null; // Reset uploaded file URL
  }

  // Stop the camera stream
  function stopVideo() {
    if (stream) {
      // @ts-ignore
      stream.getTracks().forEach(track => track.stop());
      stream = null;
      videoRef.srcObject = null; // Stop the camera stream
    }
  }

  // Handle video file upload
  /**
     * @param {{ target: { files: any[]; }; }} event
     */
  function handleFileUpload(event) {
    const file = event.target.files[0];
    if (file) {
      const url = URL.createObjectURL(file);
      stopVideo(); // Stop the camera if it's running
      videoRef.srcObject = null; // Clear any existing stream
      videoRef.src = url; // Load the uploaded video
      videoRef.play();
      uploadedFileUrl = url; // Store the URL for later use
    }
  }

  // Remove uploaded file
  function removeFile() {
    videoRef.srcObject = null; // Clear the video element
    uploadedFileUrl = null; // Reset the uploaded file URL
    fileInput.value = ''; // Clear the file input
    startVideo(); // Restart the live video
  }

  // Cleanup on component destruction
  onMount(() => {
    startVideo();
  });

  onDestroy(() => {
    stopVideo();
  });
</script>

<style>
  video {
    width: 100%;
    max-width: 600px;
    margin: 1rem 0;
    border: 1px solid #ccc;
    border-radius: 8px;
  }
  .controls {
    margin-top: 1rem;
  }
</style>

<div>
  <h2>Camera and Video Upload</h2>
  <video bind:this={videoRef} autoplay></video>
  <div class="controls">
    <input type="file" accept="video/*" bind:this={fileInput} on:change={handleFileUpload} />
    <button on:click={stopVideo}>Stop Camera</button>
    <button on:click={startVideo}>Capture Live Video</button>
    {#if uploadedFileUrl}
      <button on:click={removeFile}>Remove File</button>
    {/if}
  </div>
  <p>Upload a video file to analyze or use your camera for live capture.</p>
</div>
