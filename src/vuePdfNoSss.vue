<style src="./annotationLayer.css"></style>
<script>

	import componentFactory from './componentFactory.js'


	var pdfjsWrapper = require('./pdfjsWrapper.js').default;
	var PDFJS = require('pdfjs-dist/build/pdf.js');

	if ( typeof window !== 'undefined' && 'Worker' in window && navigator.appVersion.indexOf('MSIE 10') === -1 ) {
		var PdfjsWorker = require('pdfjs-dist/build/pdf.worker.js');
		// PDFJS.GlobalWorkerOptions.isWorkerDisabled = true;
		// PDFJS.GlobalWorkerOptions.workerSrc = '/service.worker.js';

		PDFJS.GlobalWorkerOptions.workerPort = new PdfjsWorker();
	}

	var component = componentFactory(pdfjsWrapper(PDFJS));


	export default component;
</script>
