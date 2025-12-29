
> **metalToolChain error fix**

**Solution 1 :** [Ref](https://support.circleci.com/hc/en-us/articles/40865586354971-Resolving-Metal-Toolchain-Execution-Missing-Error-in-Xcode-26)
1. Download : 
	1. ```xcodebuild -downloadComponent metalToolchain -exportPath /tmp/MetalExport/```
2. Modify and export data
	1. `sed -i '' -e 's/17A5295f/17A5241e/g' /tmp/MetalExport/MetalToolchain-17A5295f.exportedBundle/ExportMetadata.plist`
3. Import the Metal Toolchain
	1. `1. xcodebuild -importComponent metalToolchain -importPath /tmp/MetalExport/MetalToolchain-17A5295f.exportedBundle`

