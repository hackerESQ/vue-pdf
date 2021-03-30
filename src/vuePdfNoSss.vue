<style src="./annotationLayer.css"></style>
<script>
console.log('test-1')

	import componentFactory from './componentFactory.js'

console.log('test0')
	if ( process.env.VUE_ENV !== 'server' ) {
console.log('test1')
		var pdfjsWrapper = require('./pdfjsWrapper.js').default;
		var PDFJS = require('pdfjs-dist/es5/build/pdf.js');

		if ( typeof window !== 'undefined' && 'Worker' in window && navigator.appVersion.indexOf('MSIE 10') === -1 ) {
console.log('test2')
			var PdfjsWorker = require('pdfjs-dist/es5/build/pdf.worker.js');
			PDFJS.GlobalWorkerOptions.isWorkerDisabled = true;
			PDFJS.GlobalWorkerOptions.workerSrc = '/service.worker.js';
			
			// PDFJS.GlobalWorkerOptions.workerPort = new PdfjsWorker();
		}

		var component = componentFactory(pdfjsWrapper(PDFJS));
	} else {

		var component = componentFactory({});
	}

	export default component;
</script>
