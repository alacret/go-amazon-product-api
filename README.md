# Go Amazon Product API Wrapper

## This library was forked from https://github.com/DDRBoxman/go-amazon-product-api

Simple library to simplify grabbing and posting data from the Amazon Affiliate API


Example
_______

	package main

	import (
		"fmt"
		"net/http"
		"encoding/xml"
		"github.com/alacret/go-amazon-product-api"
	)

	func main() {
		var api amazonproduct.AmazonProductAPI

		api.AccessKey = ""
		api.SecretKey = ""
		api.Host = "webservices.amazon.com"
		api.AssociateTag = ""
		api.Client = &http.Client{} // optional

		result,err := api.ItemSearchByKeyword("sgt+frog", 0)
		if (err != nil) {
			fmt.Println(err)
		}

		fmt.Println(result)


		//Parse result
		if err == nil {
			aws := new(amazonproduct.ItemSearchResponse)
			xml.Unmarshal([]byte(result), aws)
		}
	}

