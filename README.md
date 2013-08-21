
# IGHTMLQuery

IGHTMLQuery is a lightweight XML/HTML parser for iOS, built on top of libxml.

## Features

- XPath support for document searching.
- jQuery style chainable syntax.
- XML traversal and manipulation.

## Why do we need yet another XML library?

I need a clean, simple, familiar and powerful library to query and manipulate HTML documents. 

Consider following snippets:

```objective-c
IGXMLDocument* node = [[IGXMLDocument alloc] initWithXMLString:catelogXml encoding:NSUTF8StringEncoding error:nil];
NSString* title = [[[node queryWithXPath:@"//cd/title"] firstObject] text];
[[node queryWithXPath:@"//title"] enumerateNodesUsingBlock:^(IGXMLNode *node, NSUInteger idx, BOOL *stop) {
    XCTAssertTrue((NSInteger)[artists indexOfObject:node.text] > -1, @"should be valid artist");
}];

// or using jquery style shortcut
NSString* title = node.query(@"//cd/title").firstObject.text;
node.query(@"//cd/title").each(^(IGXMLNode* node){ 
  NSLog(@"%@", node.text);
})

// quick manipulation
node.query(@"//cd/title").append(@"&lt;message&gt;Hi!&lt;/message&gt;")
```

## Usage

TBA

## License

MIT License.